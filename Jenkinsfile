pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-project:v1 .'
            }
        }

        stage('Remove Old Container') {
            steps {
                sh 'docker rm -f manojclouds || true'
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d --name manojclouds -p 80:80 devops-project:v1'
            }
        }
    }
}
