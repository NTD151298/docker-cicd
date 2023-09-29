pipeline {
  agent any
  stages {
    stage('From github') {
      step {
        script{
          git branch: 'main', credentialsId: 'duong-admin', url: 'https://github.com/NTD151298/docker-cicd'
        }
      }
    }
    stage('Build and push docker to docker hub') {
      step {
        script{
          withDockerRegistry(credentialsId: 'docker-new-hub-bro', url: 'https://index.docker.io/v1/') {
            powershell 'sudo docker build -t duongtn1512/random_game:pingpong2 .'
            powershell 'sudo docker push -t duongtn1512/random_game:pingpong2 '
          }
        } 
      }
    }
  }
}
