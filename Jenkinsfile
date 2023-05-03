pipeline {
    agent any
    
    
  options {
    skipDefaultCheckout(true)
  }

   
    stages {
        stage('git checkout') {
            steps {
                script {
                    checkout scm
                    }
                
            }
        }

        stage('Unit test') {
            steps {
                script {
                    sh '''
                    pip install -r requirements.txt
                    python3.9 manage.py test
                    '''
                }
            }
        }
        
        stage('Docker compose') {
            steps {
                script {
                    sh '''
                docker compose stop || true
                docker compose up -d 
                '''
                }
            }
        }
    }
}
