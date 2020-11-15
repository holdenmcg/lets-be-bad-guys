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
      environment {
        PATH = '"/usr/local/bin/:$PATH"'
      }
      steps {
        echo "PATH is: $PATH"
      }
    }

  }
  environment {
    PATH = "/usr/local/bin/:$PATH"
  }
}