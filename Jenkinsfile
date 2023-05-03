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
    stage('Docker stop') {
      steps {
        sh 'docker stop react'
      }
    }
    stage('Docker start') {
      steps {
        sh 'docker run -d -e PORT="80" -p "80:80" --name "react" silinfo/jenkins-example-react'
      }
    }
  }
}