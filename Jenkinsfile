pipeline {
    agent any

    stages {
        
        stage('DEV_DEPLOY'){
            steps{
            sh 'mvn clean package'
            sh 'docker build -t sgb-jenkins-task3:latest .'
            }
        }

        stage ('Prompt for input') {
            steps {
                script {
                    env.TAGNAME = input message: 'Please enter the tag name', parameters: [string(defaultValue: 'latest',description: '')]
                }
                echo "Username: ${env.TAGNAME}"
            }
            input{
                message 'Deploy image?'
                ok "Approve!"
            }
        }

        stage('CLEANUP'){
            steps{
                sh 'docker image prune --all'
            }
        }
    }
}