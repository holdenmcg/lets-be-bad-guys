pipeline {
  agent {
    docker {
      image 'returntocorp/semgrep-agent:v1'
    }

  }
  stages {
    stage('Semgrep-agent') {
      steps {
        sh 'cd /app; python -m semgrep_agent '
      }
    }

  }
}