pipeline {
    agent any

    environment {
        // Define environment variables
      // DOCKER_IMAGE = 'your-docker-image:latest'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout your source code from version control
               //  checkout scm
                         https://github.com/Veenayadav02/jenkinspipeline4docker.git
            }
        }

        stage('Build and Push Docker Image') {
            steps {
                script {
                    // Build Docker image and tag it
                    docker.build -t pipelineimg .

                    // Push the Docker image to a container registry (e.g., Docker Hub)
                   // docker.withRegistry('https://registry.example.com', 'registry-credentials') {
                      //  docker.image(env.DOCKER_IMAGE).push()
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                // Deploy the Docker image to your environment (e.g., Kubernetes, Docker Compose, etc.)
                script {
                     docker run -it pipelineimg
                }
            }
        }

        stage('Test') {
            steps {
                // Add test steps here if needed
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
