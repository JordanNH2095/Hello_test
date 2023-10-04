pipeline {
  agent {
    docker {
      image 'node:18.17.1-alpine3.18'
      args '-p 3000:3000'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh ' sh \'npm install\''
      }
    }

    stage('Test') {
      steps {
        sh ' sh \'./jenkins/scripts/test.sh\''
      }
    }

    stage('Deliver') {
      steps {
        sh '''sh \'./jenkins/scripts/deliver.sh\'
input message: \'Finished using the web site? (Click "Proceed" to continue)\' 
sh \'./jenkins/scripts/kill.sh\' '''
      }
    }

  }
}