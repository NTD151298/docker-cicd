pipeline {
  agent any
  stages {
    stage('From github') {
      steps {
        // Lấy mã nguồn từ GitHub
        git branch: 'main', credentialsId: 'duong-admin', url: 'https://github.com/NTD151298/docker-cicd'
      }
    }
    stage('Build and push docker to docker hub') {
      steps {
        // Xây dựng và đẩy Docker image
        withDockerRegistry(credentialsId: 'docker-new-hub-bro', url: 'https://index.docker.io/v1/') {
          sh 'docker build -t duongtn1512/random_game:pingpong2 .'
          sh 'docker push -t duongtn1512/random_game:pingpong2 '
        } 
      }
    }
  }
}
//pipeline {
//    agent any
//    stages {
//        stage('Checkout') {
//            steps {
//                // Lấy mã nguồn từ GitHub
//                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/NTD151298/docker-cicd']]])
//            }
//        }
//        stage('Build Docker Image') {
//          steps {
//            script {
//              def dockerImage = docker.build('duongtn1512/random_game:pingpong2', '.')
//              dockerImage.inside('-v /var/run/docker.sock:/var/run/docker.sock') {
//                sh 'docker build -t duongtn1512/random_game:pingpong2 .'
//              }
//            }
//          }
//        }
//    }
//}
//pipeline {
//  agent any
//  stages {
//    stage('From github') {
//      step {
//        git branch: 'main', credentialsId: 'duong-admin', url: 'https://github.com/NTD151298/docker-cicd'
//      }
//    }
//    stage('Build and push docker to docker hub') {
//      step {
//        withDockerRegistry(credentialsId: 'docker-new-hub-bro', url: 'https://index.docker.io/v1/') {
//          sh 'docker build -t duongtn1512/random_game:pingpong2 .'
//          sh 'docker push -t duongtn1512/random_game:pingpong2 '
//        } 
//      }
//    }
//  }
//}

