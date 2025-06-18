pipeline {
    agent any

    environment {
        IMAGE_NAME = 'galeri'
    }

    stages {
        stage('Build Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME:latest .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh 'docker stop $IMAGE_NAME || true'
                sh 'docker rm $IMAGE_NAME || true'
                sh 'docker run -d --name $IMAGE_NAME -p 8081:80 $IMAGE_NAME:latest'
            }
        }

        stage('Monitor Storage') {
            steps {
                sh 'df -h'
            }
        }
    }
}
