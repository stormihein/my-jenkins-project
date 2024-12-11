pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Example: Install dependencies for a Node.js app
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                // Example: Run tests
                sh 'npm test'
            }
        }

        stage('Deploy') {
            steps {
                // Example: Deploy to a remote server or copy files
                echo 'Deploying application...'
                // Replace this with your actual deployment command
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
