pipeline {
    agent any

    stages {
        stage('PROMPT INPUT'){
            steps{
                script{
                    env.tagvalue = input message: 'Please enter the build tag value', parameters: [string(defaultValue: '', description: '', name: 'tagvalue')]
                }          
            }
            input{
                message "Should approve ?"
                ok "Approve"
            } 
        }
        stage('DEV_DEPLOY'){
            steps{
                sh 'mvn clean package'
                sh "docker build -t sgb-jenkins-task3:${env.tagvalue} ."   
            }
        }
        stage('QA_DEPLOY'){
            steps{
                echo 'deploy approved'
            } 
        }
        stage('CLEANUP'){
            steps{
                sh 'docker image prune -f --all'
            }
        }
    }
}