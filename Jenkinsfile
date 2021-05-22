pipeline {
    agent any
    stages {
        stage("Pull Latest Image") {
            steps {
                sh "docker pull aadithyaks/selenium-docker"
            }
        }
        stage("Start Grid") {
            steps {
                sh "docker-compose up -d hub chrome firefox"
            }
        }
        stage("Run Tests") {
            steps {
                sh "docker-compose up spethomepage-module spetsearchpage-module"
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: 'output/**'
            sh "docker-compose down"
            sh "sudo rm -rf output/"
        }
    }
}