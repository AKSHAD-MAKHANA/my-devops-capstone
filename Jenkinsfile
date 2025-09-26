pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/AKSHAD-MAKHANA/my-devops-capstone.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t mydockerapp .'
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    // Stop old container if running
                    sh 'docker rm -f capstone-app || true'
                    // Run new container
                    sh 'docker run -d -p 8081:80 --name capstone-app mydockerapp'
                }
            }
        }

        stage('Verify') {
            steps {
                script {
                    sh 'curl -s http://localhost:8081'
                }
            }
        }
    }
}

