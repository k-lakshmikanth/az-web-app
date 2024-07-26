pipeline {
    agent any

    stages {
        stage('Git checkout') {
            steps {
                git changelog: false, poll: false, url: 'https://github.com/k-lakshmikanth/az-web-app.git'
            }
        }
        stage('build & push docker image') {
            steps {
                script{
                    withDockerRegistry(credentialsId: '08be3f04-0f14-43e4-a55a-bc9a2577a236') {
                        powershell "docker build -t az-web-app:latest ."
                        powershell "docker tag az-web-app klakshmikanth/az-web-app:latest"
                        powershell "docker push klakshmikanth/az-web-app:latest"
                    }
                }
            }
        }
    }
}
