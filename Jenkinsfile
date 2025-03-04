pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'pravalikaa18/my_project:latest'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git url:'https://github.com/pravalikaa18/jenkins_docker.git',branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }

        stage('Push Docker Image') {
            steps {
                withDockerRegistry([credentialsId: '395ce1a5-6982-4c78-9994-4a2e8dbce27a', url: 'https://index.docker.io/v1/']) {
                    sh 'docker push $DOCKER_IMAGE'
                }
            }
        }
    }
}
