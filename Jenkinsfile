pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'dev', url: 'https://github.com/MohamedMagdy840/jenkins-repo.git'
                // Replace with your repository URL
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build Docker image with a tag (e.g., myapp:latest)
                    sh 'docker build -t myapp:latest .'
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    // Run Docker image and show running containers
                    sh '''
                        docker run --name myapp-container -d myapp:latest
                        docker ps
                    '''
                }
            }
        }
    }
}
