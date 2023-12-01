pipeline {
    agent any

    stages {
        stage('Git') {
            steps {
                script {
                    // Build Docker image
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
