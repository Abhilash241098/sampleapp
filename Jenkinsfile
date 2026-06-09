pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Image') {
            steps {
                sh '''
                docker build -t my-web-app:latest .
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                docker rm -f my-web-app || true

                docker run -d \
                  --name my-web-app \
                  -p 80:80 \
                  my-web-app:latest
                '''
            }
        }
    }
}
