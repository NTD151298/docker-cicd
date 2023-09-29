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
            script {
              def dockerImage = docker.build('duongtn1512/random_game:pingpong2', '.')
              dockerImage.inside('-v /var/run/docker.sock:/var/run/docker.sock') {
                sh 'docker build -t duongtn1512/random_game:pingpong2 .'
              }
            }
          }
        }
    }
}
