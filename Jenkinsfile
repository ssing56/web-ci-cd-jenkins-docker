pipeline {
    agent any

    environment {
        AWS_REGION = "us-east-1"
        ECR_REPO = "815470165173.dkr.ecr.us-east-1.amazonaws.com/web-ci-cd-jenkins-docker"
        IMAGE_NAME = "webapp-ci"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/ssing56/web-ci-cd-jenkins-docker.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Login to ECR') {
            steps {
                sh '''
                aws ecr get-login-password --region $AWS_REGION | \
                docker login --username AWS --password-stdin 815470165173.dkr.ecr.us-east-1.amazonaws.com
                '''
            }
        }

        stage('Push Image to ECR') {
            steps {
                sh '''
                docker tag $IMAGE_NAME:latest $ECR_REPO:latest
                docker push $ECR_REPO:latest
                '''
            }
        }

        stage('Deploy to EKS') {
            steps {
                sh '''
                kubectl apply -f deployment.yaml
                kubectl apply -f service.yaml
                '''
            }
        }
    }
}

