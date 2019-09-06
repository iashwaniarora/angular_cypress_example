pipeline {
    agent any

    tools {nodejs "node"}

    environment {
        CHROME_BIN = 'C:\\Program Files (x86)\\Google\\Chrome\\Application\\chrome.exe'
    }

    stages {
        stage('Dependencies') {
            steps {
               echo 'starting stage Dependencies....'
                
            }
        }
        stage('Build') {
            steps {
                  echo 'starting stage Build....'
                bat 'node -v'
                bat 'npm run build'
            }
        }
        stage('Unit Tests') {
            steps {
            echo 'starting stage Unit Tests....'
               
            }
        }
        stage('e2e Tests') {
            steps {
                bat 'npm run cypress:ci'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }

    post {
        always {
            junit 'results/cypress-report.xml'
        }
    }
}
