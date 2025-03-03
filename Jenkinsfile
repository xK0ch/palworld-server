pipeline {
    agent any

    environment {
        PALWORD_SERVER_PASSWORD = credentials('palworld-server-password')
        PALWORLD_SERVER_ADMIN_PASSWORD = credentials('palworld-server-admin-password')
    }

    stages {
        stage('Deploy') {
            steps {
                script {
                    withEnv(["PALWORD_SERVER_PASSWORD=${PALWORD_SERVER_PASSWORD}", "PALWORLD_SERVER_ADMIN_PASSWORD=${PALWORLD_SERVER_ADMIN_PASSWORD}"]) {
                        sh 'docker compose -f docker-compose-palworld-server.yml down'
                        sh 'docker image prune -af'
                        sh 'docker compose -f docker-compose-palworld-server.yml up -d'
                    }
                }
            }
        }
    }
}