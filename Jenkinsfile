pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // Lấy mã nguồn từ GitHub
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/NTD151298/docker-cicd']]])
            }
        }
        stage('Build Docker Image') {
            steps {
                // Xây dựng Docker image từ Dockerfile trong thư mục hiện tại
                script {
                    def dockerImage = docker.build('duongtn1512/random_game:pingpong2', '.')
                }
            }
        }
    }
}
