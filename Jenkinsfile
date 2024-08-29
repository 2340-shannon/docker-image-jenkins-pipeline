pipeline {
    agent any
    tools{
     jdk 'Java17'
    }
    stages {
        stage('Clean workspace and Navigate to the folder'){
            steps{
                cleanWs()
                bat 'copy C:\\Users\\Student\\Documents\\2315  C:\\Users\\Student\\AppData\\Local\\Jenkins\\.jenkins\\workspace\\pipelining'
            }
        }
        stage('Build') {
            steps {
                bat 'javac Pattern.java'
            }
        }
        stage('Jar') {
            steps {
                bat 'jar cfe myJar.jar Pattern Pattern.class'
            }
        }
        stage('Run') {
            steps {
                bat 'java -jar myJar.jar'
            }
        }
        stage('Artifact'){
            steps{
                archiveArtifacts artifacts: '*.jar', followSymlinks: false
            }
        }
    }
}