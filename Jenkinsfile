pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'dushyant05/my-flask-app'
        DOCKER_CREDENTIALS_ID = 'dockerhub-creds'  
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/Dushyant-1/Python-assessment.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build(DOCKER_IMAGE)
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', DOCKER_CREDENTIALS_ID) {
                        docker.image(DOCKER_IMAGE).push('latest')
                    }
                }
            }
        }
    }
}
