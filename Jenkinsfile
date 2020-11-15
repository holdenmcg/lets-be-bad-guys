pipeline {
  agent none
  stages {
    stage('Docker node test') {
      agent {
        docker {
          image 'node:7-alpine'
          args '--name docker-node'
        }

      }
      steps {
        sh 'node --version'
      }
    }

  }
}