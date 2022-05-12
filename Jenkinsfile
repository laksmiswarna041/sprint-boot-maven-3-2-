pipeline {
    agent any

    stages {
        
        stage('DEV_DEPLOY'){
            steps{
            sh 'mvn clean package'
            sh 'docker build -t sgb-jenkins-task3:latest .'
            }
        }

        stage('QA DEPLOY'){
            input{
                   message: 'Enter tage name to deploy image'
                   parameters:[
                       [$class: 'GlobalVariableStringParameterDefinition',defaultValue: 'latest']
                   ]
               }
            steps{
                echo "Deploying image with tag: ${env.tag_name}"
            }
        }

        stage('CLEANUP'){
            steps{
                sh 'docker image prune --all'
            }
        }
    }
}