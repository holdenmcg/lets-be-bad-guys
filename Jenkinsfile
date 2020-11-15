pipeline {
  agent any
  stages {
    stage('build') {
      agent {
        docker {
          image 'node:7-alpine'
          args '--name docker-node'
        }

      }
      steps {
        echo "PATH is: $PATH"
      }
    }

  }
}