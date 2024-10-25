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
                    bat 'docker build -t ubuntu .'
                }
            }
        }
        stage('Run Docker Container') {
            steps {
                script {
                    // Running the Docker container in daemon mode
                    bat 'docker run -d --name 2340 ubuntu'
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
