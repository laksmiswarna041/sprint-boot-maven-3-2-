pipeline {
    agent any

    stages {
        stage("User input"){
            steps{
                script{
                    env.tag_name = input message: 'Enter tag name'
                }
                echo "Deploying image with tag: ${env.tag_name}"
            }
        }
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