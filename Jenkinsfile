pipeline {
    agent any

    stages {
        stage('Deploy') {
            steps {
                script {
                    sh 'docker compose -f docker-compose-palworld-server.yml down'
                    sh 'docker image prune -af'
                    sh 'docker compose -f docker-compose-palworld-server.yml up -d'
                }
            }
        }
    }
}