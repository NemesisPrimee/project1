pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t project1:latest .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                    docker rm -f project1 || true

                    docker run -d \
                        --name project1 \
                        -p 5000:5000 \
                        project1:latest
                '''
            }
        }
    }
}
