pipeline{
    agent any
    stages{
        stage("Pull Latest Image") {
            sh "docker pull sacstone/selenium-docker"
        }
        stage("Start Grid"){
            steps{
                sh "docker-compose up -d hub chrome firefox"
            }
        }
        stage("Run Tests"){
            steps{
                sh "docker compose up search-module"
            }
        }

    }
    post{
        always{
           // archiveArtifacts artifacts: 'output/**'
            sh "docker-compose down"
        }
        


    }


}

