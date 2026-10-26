
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
                echo 'Code downloaded from GitHub'
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t asd-web-app .'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker rm -f asd-web-app || true'
                sh 'docker run -d --name asd-web-app -p 8081:80 asd-web-app'
            }
        }

        stage('Verify') {
            steps {
                sh 'docker ps'
                sh 'curl -f http://localhost:8081'
            }
        }
    }
}
