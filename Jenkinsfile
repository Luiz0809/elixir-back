pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'luiz0809/elixir-back'
        PORT = '9090'
    }

    stages {
        stage('Deploy') {
            steps {
                script {
                        sh "docker pull ${DOCKER_IMAGE}"
                        sh "docker run -d -p ${PORT}:8080 ${DOCKER_IMAGE}"
                }
            }
        }
    }
}
