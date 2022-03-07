pipeline {
  
  agent any
  
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub-tarsoqueiroz')
  }
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t tarsoqueiroz/dp-alpine:latest .'
      }
    }
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Push') {
      steps {
        sh 'docker push tarsoqueiroz/dp-alpine:latest'
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}
