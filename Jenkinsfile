pipeline {
    agent any
    environment {
        DOCKER_HUB_CREDENTIALS = credentials('dockerhub-credentials')
    }
    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/akshat122001/JenkinsDocker.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    def app = docker.build("akshat122001/sample-node-app")
                }
            }
        }
        stage('Push Docker Image to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', DOCKER_HUB_CREDENTIALS) {
                        def app = docker.build("akshat122001/sample-node-app")
                        app.push('latest')
                    }
                }
            }
        }
    }
}
