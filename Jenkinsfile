pipeline {
    agent any

    stages {
        stage('Set Permissions') {
            steps {
                script {
                    // You might need to set up Docker permissions properly.
                    // For example, adding the Jenkins user to the Docker group:
                    // sh 'sudo usermod -aG docker jenkins'
                }
            }
        }

        stage('Git Checkout') {
            steps {
                script {
                    git 'https://github.com/Veenayadav02/jenkinspipeline4docker.git'
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    // Run tests if needed
                    sh 'docker build -t pythonubuntu .'
                }
            }
        }

        stage('Run') {
            steps {
                script {
                    // Deploy the Docker image as needed
                    sh 'docker run -i pythonubuntu'
                }
            }
        }
    }
}
