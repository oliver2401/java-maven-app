pipeline {   
    agent any
    stages {
        stage("test") {
            steps {
                script {
                    echo "Testing the application...."
                    echo "executing pipeline on branch: $BRANCH_NAME"
                }
            }
        }
        
        stage("build") {
            when {
                expression { 
                    BRANCH_NAME == "main" 
                }
            }
            steps {
                script {
                    echo "Building the application...."
                }
            }
        }

        stage("deploy") {
            /*when {
                expression { 
                    BRANCH_NAME == "main" 
                }
            }*/
            steps {
                script {
                    def dockerCmd = 'docker run -p 3080:3080 -d oliver2401/demo-app:1.0'
                    sshagent(['ec2-server-key']) {
                       sh "ssh -o StrictHostKeyChecking=no ec2-user@3.89.102.151 ${dockerCmd}"      
                    }
                }
            }               
        }
    }
} 
