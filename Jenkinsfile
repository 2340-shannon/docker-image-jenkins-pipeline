pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // Cloning the repository
                git 'https://github.com/2340-shannon/docker-image-jenkins-pipeline'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    // Building the Docker image
                    sh 'docker build -t myapp:latest .'
                }
            }
        }
        stage('Run Docker Container') {
            steps {
                script {
                    // Running the Docker container in daemon mode
                    sh 'docker run -d --name myapp-container myapp:latest'
                }
            }
        }
    }
    post {
        always {
            // Cleanup or notification steps
            echo 'Pipeline execution completed.'
        }
    }
}
