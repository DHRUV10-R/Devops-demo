
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                bat 'docker build -t devops-demo:1.0 C:\\devops-practical'
            }
        }

        stage('Test') {
            steps {
                bat 'docker image inspect devops-demo:1.0'
            }
        }

        stage('Deploy') {
            steps {
                bat 'docker rm -f devops-demo 2>NUL & docker run -d --name devops-demo -p 8085:80 devops-demo:1.0'
            }
        }

        stage('Verify') {
            steps {
                bat 'docker ps --filter name=devops-demo'
                bat 'curl.exe --retry 5 --retry-delay 2 --retry-connrefused --fail http://localhost:8085'
            }
        }
    }
}
