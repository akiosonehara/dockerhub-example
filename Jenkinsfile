pipeline {
  
  agent { label 'linux' }
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub-cred-bernardo9999')
  }
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t bernardo9999/dp-alpine:latest .'
      }
    }
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Push') {
      steps {
        sh 'docker push bernardo9999/dp-alpine2:latest'
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}
