pipeline {
  agent any
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub')
  }
  stages {
    stage('Build') {
      steps {
        echo "Now we will start building docker image"
        sh 'docker build -t duongtn1512/random_game:pingpong5 .'
        echo "Our image are successly build with tag pingpong5"
      }
    }
    stage('Login') {
      steps {
        echo "Enterning our dockerhub user name and password"
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
        echo "Login success"
      }
    }
    stage('Push') {
      steps {
        echo "We are pushing now"
        sh 'docker push duongtn1512/random_game:pingpong5'
        echo "Push to doker registry done"
      }
    }
  }
  post {
    always {
      sh 'docker logout'
      echo "Logout docker"
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