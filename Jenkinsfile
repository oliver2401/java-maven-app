pipeline {   
    agent any
    stages {
        stage("test") {
            steps {
                script {
                    echo "Testing the application...."
                    echo "executing pipeline on branch: $BRANCH_NAME"
                    echo "adding webhook"
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
            when {
                expression { 
                    BRANCH_NAME == "main" 
                }
            }
            steps {
                script {
                    echo "Deploying the application...."
                }
            }
        }               
    }
} 
