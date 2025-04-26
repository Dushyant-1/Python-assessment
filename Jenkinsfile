pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-creds')  // Your Docker Hub credentials in Jenkins
        IMAGE_NAME = 'dushyant05/my-flask-app'  // Your Docker Hub repo name
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/Dushyant-1/Python-assessment.git'  // Your GitHub repo URL
            }
        }

        stage('Build Docker Image') {
            steps {
                bat "docker build -t %IMAGE_NAME% ."  // Build the Docker image
            }
        }

        stage('Login to Docker Hub') {
            steps {
                bat "echo %DOCKERHUB_CREDENTIALS_PSW% | docker login -u %DOCKERHUB_CREDENTIALS_USR% --password-stdin"  // Docker login command
            }
        }

        stage('Push Image to Docker Hub') {
            steps {
                bat "docker push %IMAGE_NAME%"  // Push the Docker image to Docker Hub
            }
        }
    }

    post {
        success {
            echo 'Docker image built and pushed successfully!'  // Success message
        }
        failure {
            echo 'Pipeline failed.'  // Failure message
        }
    }
}
