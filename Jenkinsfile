pipeline {
    agent any

    stages {
        stage('DEV DEPLOY'){
            steps{
            sh 'mvn clean package'
            sh 'docker build -t sgb-jenkins-task3:latest .'
            }
        }

        stage('QA DEPLOY'){
            input{
                message "Enter tag name for image"
            }
            steps{
                echo "Build tag updated"   
            }
        }

         stage('CLEANUP'){
            steps{
                sh 'docker image prune --all'
            }
        }
    }
}