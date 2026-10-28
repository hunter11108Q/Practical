
pipeline {
    agent any

    triggers {
        pollSCM('H/5 * * * *')
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Fetching source code from GitHub'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building the project'
                bat 'dir'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing the project'
                bat 'if exist Jenkinsfile (echo Jenkinsfile found) else (exit /b 1)'
            }
        }

        stage('Success') {
            steps {
                echo 'Continuous Integration completed successfully!'
            }
        }
    }
}
