pipeline {
  agent any
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub')
  }
  stages {
    stage('Build') {
      steps {      
        echo "Building..."
        sh 'docker build -t duongtn1512/random_game:pingpong99 .'       
      }
    }
    stage('Login') {
      steps {        
        echo "Login to Docker hub..."
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Push') {
      steps {
        echo "Pusing newest image are getting push to dockerhub ..."
        sh 'docker push duongtn1512/random_game:pingpong99'
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}
//pipeline {
//  agent any
//  stages {
//        stage('Build and Push Docker Image') {
//        steps {
//            withDockerRegistry(credentialsId: 'dockerhub', url: 'https://index.docker.io/v1/') {
//              sh 'docker build -t duongtn1512/random_game:pingpong3 .'
//              sh 'docker push duongtn1512/random_game:pingpong3 '
//        } 
//        }
//    }
//  }
//}