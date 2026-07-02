pipeline {
    agent any

    stages {
        stage('Clone Code') {
            steps {
                git branch: 'main', url: 'https://github.com/ManojPrabhahar/Project-practice-Manoj-Prabhahar.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t manojprabhahar/devops-project:v1 .'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                    sh 'docker push manojprabhahar/devops-project:v1'
                }
            }
        }
    }
}

