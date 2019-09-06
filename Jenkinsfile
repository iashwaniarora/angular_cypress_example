pipeline {
    agent any

    tools {nodejs "node"}

    environment {
        CHROME_BIN = '/bin/google-chrome'
    }

    stages {
        stage('Dependencies') {
            steps {
               echo 'starting stage Dependencies....'
                bat 'npm i'
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
                bat 'npm run test'
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
