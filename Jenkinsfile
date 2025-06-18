pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/NAMA_KAMU/galeri-foto.git'
            }
        }

        stage('Build Image') {
            steps {
                sh 'docker build -t galeri:latest .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh 'docker stop galeri || true'
                sh 'docker rm galeri || true'
                sh 'docker run -d --name galeri -p 8081:80 galeri:latest'
            }
        }

        stage('Monitor Storage') {
            steps {
                sh 'df -h > storage.txt'
                sh 'cat storage.txt'
            }
        }
    }
}
