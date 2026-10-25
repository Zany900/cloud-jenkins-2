
pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t cloud-jenkins-2:v1 -f dockerfile .'
            }
        }

        stage('Deploy Website') {
            steps {
                sh 'docker rm -f cloud-jenkins-2-container || true'
                sh 'docker run -d --name cloud-jenkins-2-container -p 8081:80 cloud-jenkins-2:v1'
            }
        }

    }
}

