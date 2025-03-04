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
                withDockerRegistry([credentialsId: '5876666f-40b4-4751-8ae0-658b792dd15e', url: 'https://index.docker.io/v1/']) {
                    sh 'docker push $DOCKER_IMAGE'
                }
            }
        }
    }
}
