pipeline {
  agent {
    docker {
      image 'returntocorp/semgrep-agent:v1'
    }

  }
  stages {
    stage('Semgrep-agent') {
      steps {
        sh '/root/.local/bin/semgrep --version '
      }
    }

  }
}