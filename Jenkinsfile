pipeline {
  agent {
    docker {
      image 'returntocorp/semgrep-agent:v1'
    }

  }
  stages {
    stage('Semgrep') {
      steps {
        sh 'cat /etc/alpine-release'
      }
    }

  }
}