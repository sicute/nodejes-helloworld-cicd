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
          stage('Push Image') {
              steps{
                  script 
                    {
                        docker.withRegistry( '', registryCredential ) {
                            dockerImage.push()
                        }
                   } 
               }
            }
        #stage('Deploying into k8s')
        #{
        #    steps{
        #        sh 'kubectl apply -f deployment.yml'
        #    }
        #}
    }
}
