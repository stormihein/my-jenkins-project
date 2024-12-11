pipeline {
    agent any

    environment {
        DOCKER_HUB_CREDENTIALS = credentials('dockerhub-credentials-id') // Your created credentials ID
    }

    stages {
        stage('Checkout') {
            steps {
                // Pull code from the repository
                git branch: 'main', url: 'https://github.com/stormihein/my-jenkins-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                // Build the Docker image
                sh 'docker build -t stormihein/my-jenkins-app .'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                // Log in to Docker Hub and push the image
                withCredentials([usernamePassword(credentialsId: 'dockerhub-credentials-id', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
                    sh 'echo $DOCKER_PASSWORD | docker login -u $DOCKER_USERNAME --password-stdin'
                    sh 'docker push stormihein/my-jenkins-app'
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution completed.'
        }
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
