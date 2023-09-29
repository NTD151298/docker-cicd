pipeline {
    agent any

    stages {
        stage('Install Docker') {
            steps {
                script {
                    sh 'curl -fsSL https://get.docker.com | sh'
                    sh 'usermod -aG docker jenkins'
                    sh 'docker run -d --name jenkins -v /var/run/docker.sock:/var/run/docker.sock -p 8080:8080 jenkins/jenkins:lts'
                }
            }
        }

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
                        def dockerImage = docker.build('duongtn1512/random_game:pingpong2', '.')
                        dockerImage.push()
                    }
                }
            }
        }
    }
}
