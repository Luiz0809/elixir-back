pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'luiz0809/elixir-back'
    }

    stages {
        stage('Pull Docker Image') {
            steps {
                script {
                    sh "docker pull ${DOCKER_IMAGE}"
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    sh "docker run -d -p 80:8080 ${DOCKER_IMAGE}"
                }
            }
        }
    }
}
