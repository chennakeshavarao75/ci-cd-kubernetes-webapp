
pipeline {
    agent any
    environment {
        DOCKER_IMAGE = "yourusername/appname"
        TAG = "latest"
    }
    stages {
        stage('Build') {
            steps {
                script {
                    // Build Docker image
                    sh "docker build -t ${DOCKER_IMAGE}:${TAG} ."
                }
            }
        }
        stage('Push') {
            steps {
                script {
                    // Log in to Docker Hub and push the image
                    sh "docker login -u yourusername -p yourpassword"
                    sh "docker push ${DOCKER_IMAGE}:${TAG}"
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    // Update Kubernetes deployment
                    sh "kubectl set image deployment/app-deployment app=${DOCKER_IMAGE}:${TAG}"
                }
            }
        }
    }
}
