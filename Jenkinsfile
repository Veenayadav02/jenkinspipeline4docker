pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // Checkout your source code from version control
                git 'https://github.com/Veenayadav02/jenkinspipeline4docker.git'
            }
        }

        stage('Build and Push Docker Image') {
            steps {
                script {
                    // Build Docker image and tag it
                    sh 'docker.build -t ubuntuimg . '
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                // Deploy the Docker image to your environment (e.g., Kubernetes, Docker Compose, etc.)
                script {
                    sh "docker run -it ubuntuimg "
                }
            }
        }
 post {
        success {
            echo 'Pipeline succeeded!'
        }

        failure {
            echo 'Pipeline failed!'
        }

        always {
            // Clean up, if needed
            script {
                sh "docker stop \$(docker ps -q --filter ancestor=${env.DOCKER_IMAGE})"
                sh "docker rm \$(docker ps -a -q --filter ancestor=${env.DOCKER_IMAGE})"
            }
        }
    }
}    
