pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  environment {
    IMAGE_NAME = 'silinfo/jenkins-example-react'
    IMAGE_TAG = 'latest'
    APP_NAME = 'jenkins-example-react'
  }
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t $IMAGE_NAME:$IMAGE_TAG .'
      }
    }
    stage('Start') {
      steps {
        sh 'docker run -e PORT="80" -p "80:80" silinfo/jenkins-example-react'
      }
    }
  }
}