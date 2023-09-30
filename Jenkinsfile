pipeline {
  agent any
  stages {
    stage('From github') {
      steps {
        // Lấy mã nguồn từ GitHub
        git branch: 'main', credentialsId: 'github, url: 'https://github.com/NTD151298/docker-cicd'
      }
    }
    stage('Build and push docker to docker hub') {
      steps {
        // Xây dựng và đẩy Docker image
        withDockerRegistry(credentialsId: 'dockerhub', url: 'https://index.docker.io/v1/') {
          sh 'docker build -t duongtn1512/random_game:pingpong2 .'
          sh 'docker push -t duongtn1512/random_game:pingpong2 '
        } 
      }
    }
  }
}

