pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Fetching project from GitHub'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building Docker image'
                bat 'docker build -t practical-web:latest .'
            }
        }

        stage('Test') {
            steps {
                echo 'Checking Docker image'
                bat 'docker image inspect practical-web:latest'
            }
        }

        stage('Deploy using Docker') {
            steps {
                echo 'Deploying web application'

                bat '''
                    docker rm -f practical-web-container 2>NUL
                    if errorlevel 1 exit /b 1
                '''

                bat 'docker run -d --name practical-web-container -p 8081:80 practical-web:latest'
            }
        }
    }
}
