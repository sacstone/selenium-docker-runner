pipeline {
    agent any
    stages {
        stage("Start Grid") {
            steps {
                sh "docker-compose up -d hub chrome firefox"
            }
        }
        stage("Run Tests") {
            steps {
                sh "docker compose up search-module"
            }
        }
    }
    post {
        always {
            script {
                // Debug output to list the files in the artifact directory
                sh "ls -R output"

                // Archive artifacts with an updated file pattern
                archiveArtifacts artifacts: 'output/**'
            }
            sh "docker-compose down"
        }
    }
}

