pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // Cloning the repository
                bat '''git clone https://github.com/2340-shannon/docker-image-jenkins-pipeline.git
git checkout main 
'''
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    // Building the Docker image
                    bat 'docker build -t my-app:latest .'
                }
            }
        }
        stage('Run Docker Container') {
            steps {
                script {
                    // Running the Docker container in daemon mode
                    bat 'docker run -d --name my-app-container my-app:latest'
                }
            }
        }
    	stage('Push to Docker Hub') {
            steps {
                script {
                    // Login to Docker Hub
                    bat 'docker login -u dockermcauser -p #dock2024'
                    // Push the Docker image to Docker Hub
                    bat 'docker push dockermcauser/my-app:latest'
                }
            }
        }
    }
    post {
        always {
            // Cleanup or notification steps
            bat 'echo \'Pipeline execution completed.\''
        }
    }
}
