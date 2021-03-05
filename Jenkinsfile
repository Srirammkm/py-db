pipeline {
  environment {
  IBM_CLOUD_REGION = 'us-south'
  IKS_CLUSTER = 'c0uvrhfd0v1b3bd432lg'
  registry = "srirammk18/py-db"
  registryCredential = 'dockerhub_id'
  dockerImage = ''
  }
  agent any 
  stages {
    stage('Build with Docker') {
      steps {
        script {
        dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    stage('Push the image to ICR') {
      steps {
        script {
          docker.withRegistry( '', registryCredential ) {
          dockerImage.push()
          }
        }
      }
    }
  }
}
