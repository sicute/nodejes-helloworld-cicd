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