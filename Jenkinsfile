pipeline {
    agent any
    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t mydockerapp .'
            }
        }
        stage('Run Docker Container') {
            steps {
                sh 'docker rm -f capstone-app || true'
                sh 'docker run -d -p 8081:80 --name capstone-app mydockerapp'
            }
        }
    }
}
