pipeline {
    agent any

    parameters {
        // Allow user to choose between dev or main branch
        choice(
            name: 'ENV_NAME',
            choices: ['prod', 'dev'],
            description: 'Select the docker env deployment'
        )
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    git branch: "dev", url: 'https://github.com/MohamedMagdy840/jenkins-repo.git'
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build Docker image
                    sh 'docker build -t myapp:latest .'
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    // Run Docker image with build number in container name
                    sh """
                        docker run --name "${ENV_NAME}"-${BUILD_NUMBER} -d myapp:latest
                        docker ps
                    """
                }
            }
        }
    }
}
