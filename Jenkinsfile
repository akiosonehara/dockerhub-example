pipeline {
  agent any

  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub-credencial-celepar2022')
  }
  stages {
    stage('Build') {
      steps {
        sh './jenkins/build.sh'
      }
    }
    stage('Login') {
      steps {
        sh './jenkins/login.sh'
      }
    }
    stage('Push') {
      steps {
        sh './jenkins/push.sh'
      }
    }
  }
  post {
    always {
      sh './jenkins/logout.sh'
    }
  }
}
