pipeline {
  agent {
    label 'docker' 
  }
  stages {
    stage('Semgrep') {
      steps {
        sh '''echo \'Running semgrep...\'
        /usr/local/bin/docker run --rm -v "${PWD}:/src" returntocorp/semgrep --config=https://semgrep.dev/p/r2c-CI'''
      }
    }
    stage('Docker node test') {
      agent {
        docker {
          // Set both label and image
          label 'docker'
          image 'node:7-alpine'
          args '--name docker-node' // list any args
        }
      }
      steps {
        // Steps run in node:7-alpine docker container on docker slave
        sh 'node --version'
      }
    }
  }
}
