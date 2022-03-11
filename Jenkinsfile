pipeline {
  
  agent any
  
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub-credencial-celepar2022')
  }
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t celepar2022/dp-alpine-branch1:latest .'
      }
    }
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Push') {
      steps {
        sh 'docker push celepar2022/dp-alpine-branch1:latest'
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}
