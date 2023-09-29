pipeline {
  agent any
  stages {
    stage('From github') {
      steps {
        // Lấy mã nguồn từ GitHub
        script {
          git branch: 'main', credentialsId: 'duong-admin', url: 'https://github.com/NTD151298/docker-cicd'
        }
      }
    }
    stage('Build and push docker to docker hub') {
      steps {
        // Xây dựng và đẩy Docker image
        script {
          withDockerRegistry(credentialsId: 'docker-new-hub-bro', url: 'https://index.docker.io/v1/') {
            powershell 'docker build -t duongtn1512/random_game:pingpong2 .'
            powershell 'docker push -t duongtn1512/random_game:pingpong2 '
          }
        }
      }
    }
  }
}
