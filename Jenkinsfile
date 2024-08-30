pipeline {
    agent any
    tools {
        // a bit ugly because there is no `@Symbol` annotation for the DockerTool
        // see the discussion about this in PR 77 and PR 52: 
        // https://github.com/jenkinsci/docker-commons-plugin/pull/77#discussion_r280910822
        // https://github.com/jenkinsci/docker-commons-plugin/pull/52
        'org.jenkinsci.plugins.docker.commons.tools.DockerTool' '18.09'
    }
    stages {
        stage('foo') {
          steps {
            bat 'docker version' // DOCKER_CERT_PATH is automatically picked up by the Docker client
          }
        }
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
                    bat 'docker build -t myapp:latest .'
                }
            }
        }
        stage('Run Docker Container') {
            steps {
                script {
                    // Running the Docker container in daemon mode
                    bat 'docker run -d --name myapp-container myapp:latest'
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
