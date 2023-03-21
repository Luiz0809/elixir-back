pipeline {
    agent any

    environment {
        SSH_USER = 'ec2-user'
        SSH_HOST = 'xxx.xxx.xxx.xxx' // Substituir pelo endereço IP da instância EC2
        DOCKER_IMAGE = 'luiz0809/elixir-back'
        APP_NAME = 'my-elixir-app'
        PORT = '4000'
    }

    stages {
        stage('Deploy') {
            steps {
                script {
                    sshagent(['my-ssh-key']) {
                        def sshCommand = "ssh -o StrictHostKeyChecking=no ${SSH_USER}@${SSH_HOST}"
                        sh "${sshCommand} sudo docker pull ${DOCKER_IMAGE}"
                        sh "${sshCommand} sudo docker stop ${APP_NAME} || true && sudo docker rm ${APP_NAME} || true"
                        sh "${sshCommand} sudo docker run -d --name ${APP_NAME} -p ${PORT}:${PORT} ${DOCKER_IMAGE}"
                    }
                }
            }
        }
    }
}
