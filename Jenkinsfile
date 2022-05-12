pipeline {
    agent any

    stages {
        stage('DEV_DEPLOY'){
            steps{
            sh 'mvn clean package'
            sh 'docker build -t sgb-jenkins-task3:latest .'
            }
        }

        stage('QA_DEPLOY'){
            input{
                message "should approve ?"
                ok "Yes approve"
            }
            steps{
                echo 'deploy approved'
            } 
        }

        stage('CLEANUP'){
            steps{
                sh 'docker image prune --all'
            }
        }
    }
}