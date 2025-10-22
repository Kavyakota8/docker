pipeline {
    agent any

    stages {

        stage('Clean Workspace') {
            steps {
                echo 'Cleaning workspace...'
                deleteDir()
            }
        }

        stage('Checkout Code') {
            steps {
                echo 'Pulling latest code from GitHub...'
                git branch: 'main', url: 'https://github.com/Kavyakota8/SmartAppointment-DevOps.git'
            }
        }

        stage('Check Workspace Files') {
            steps {
                echo 'Verifying files in workspace...'
                bat 'dir'
                bat 'dir k8s'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Skipping Docker build on Windows for now'
            }
        }

        stage('Push Docker Image') {
            steps {
                echo 'Skipping Docker push on Windows for now'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                echo 'Deploying application to Kubernetes...'
                bat 'kubectl apply -f k8s/deployment.yaml'
                bat 'kubectl apply -f k8s/service.yaml'
            }
        }
    }

    post {
        success {
            echo 'Deployment completed successfully!'
        }
        failure {
            echo 'Deployment failed. Please check logs above.'
        }
    }
}
