pipeline {
    agent any

    stages {
        
        stage('PROMPT INPUT') {
            steps {
                script {
                         env.tagvalue = input message: 'Please enter the build tag value',
                             parameters: [string(defaultValue: '',
                                          description: '',
                                          name: 'tagvalue')]
                        }           
            }
        }
        
        stage('DEV_DEPLOY'){
            steps{
                sh 'mvn clean package'
                sh "docker build -t sgb-jenkins-task3:${env.tagvalue} ."   
            }
        }
      
        stage('QA_DEPLOY'){
            input{
                message "Should approve ?"
                ok "Approve"
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