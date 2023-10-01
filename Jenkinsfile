pipeline {
  agent any
  stages {
        stage('Build and Push Docker Image') {
        steps {
            withDockerRegistry(credentialsId: 'dockerhub', url: 'https://index.docker.io/v1/') {
              sh 'docker build -t duongtn1512/random_game:pingpong2 .'
              sh 'docker push duongtn1512/random_game:pingpong2 '
        } 
        }
    }
  }
}

