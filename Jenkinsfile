pipeline{
   tools { nodejs "nodejs14" }
  environment {
    registry = "sonjaya/nodejs-helloworld"
    registryCredential = 'dockerhub'
    dockerImage = ''
  }
  agent any
    stages {
        stage('Build'){
            steps{
                script{
                    sh "npm set audit false"
                }
               script{
                    sh "npm install"
                }
            }
        }
        stage('Building image') {
            steps{
                script {
                  dockerImage = docker.build registry + ":latest"
                }
             }
        }
    }