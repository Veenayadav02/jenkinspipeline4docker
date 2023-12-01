pipeline {
    agent any

    stages {
            stages {
        stage('1') {
            steps {
                script {
                    sh 'sudo -n chmod 666 /var/run/docker.sock'
                    // The -n option prevents sudo from prompting for a password
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
