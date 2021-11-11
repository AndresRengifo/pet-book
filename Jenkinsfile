pipeline{
  agent any
  stages{
    stage("build"){
      steps{
        nodejs(nodeJSInstallationName: 'nodejs_15_5_1'){
          sh 'npm install'
          h 'npm rebuild'
          sh "npm run build"
        }
      }
    }

    stage('deploy') {
     steps {
       nodejs(nodeJSInstallationName: 'nodejs_15_5_1') {
           withAWS(credentials: 'aws-credentials') {
               sh 'serverless deploy'
           }
       }       
     }
   }

  }
}
