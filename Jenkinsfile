pipeline {
  agent {
    docker {
      image 'node:7-alpine'
      args '--name docker-node'
    }

  }
  stages {
    stage('build') {
      steps {
        echo "PATH is: $PATH"
      }
    }

  }
  environment {
    PATH = "/usr/local/bin/:$PATH"
  }
}