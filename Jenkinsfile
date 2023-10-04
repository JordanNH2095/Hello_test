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
      parallel {
        stage('Deliver') {
          steps {
            sh '''sh \'./jenkins/scripts/deliver.sh\'
'''
          }
        }

        stage('Deliver1') {
          steps {
            sh '''input message: \'Finished using the web site? (Click "Proceed" to continue)
'''
          }
        }

        stage('Deliver2') {
          steps {
            sh 'sh \'./jenkins/scripts/kill.sh\''
          }
        }

      }
    }

  }
}