pipeline {
  agent any
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub')
    GIT_COMMIT_TAG = sh(returnStdout: true, script: "git log -n 1 --pretty=format:'%h'").trim()
    DOCKER_IMAGE_NAME = "duongtn1512/random_game"
    NEW_DOCKER_IMAGE_NAME = "duongtn1512/random_game:${GIT_COMMIT_TAG}"
  }
  stages {
    stage('Build') {
      steps {      
        echo "Building..."
        sh "docker build -t ${DOCKER_IMAGE_NAME}:${GIT_COMMIT_TAG} ."       
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
        echo "Pushing newest image to Docker Hub..."
        sh "docker push ${DOCKER_IMAGE_NAME}:${GIT_COMMIT_TAG}"
      }
    }
  }
// Stage deploy on going fixing ...
//    stage('Deploy') {
//      steps {
//        echo "Deploying to Kubernetes..."
//        withCredentials([file(credentialsId: 'kubernetes-config', variable: 'KUBE_CONFIG')]) {
//          sh """
//              echo "\$KUBE_CONFIG" > ~/.kube/config
//              kubectl apply -f kubernetes-deployment.yaml
//          """
//        }
//      }
//    }
  post {
    always {
      echo "Destroy the remain un used docker image..."
      sh 'docker image prune -f'
      echo "Logout docker..."
      sh 'docker logout'
    }
  }
}
