pipeline {
    agent any

    stages {
         stage('Build') {
            steps {
                script {
                    // Allow Jenkins to run Docker commands without sudo
                    sh 'sudo chmod 666 /var/run/docker.sock'
                    docker.build('pythonubuntu')
                }
            }
        }
        stage('Git') {
            steps {
                script {
                    // Build Docker image
                git 'https://github.com/Veenayadav02/jenkinspipeline4docker.git'
                }
            }
        }

        stage('Build1') {
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
