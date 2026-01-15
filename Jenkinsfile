pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/ssing56/web-ci-cd-jenkins-docker.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t webapp-ci .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker rm -f webapp-ci || true
                docker run -d -p 8000:80 --name webapp-ci webapp-ci
                '''
            }
        }
    }
}
