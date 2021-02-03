pipeline {
  agent {
    docker {
      image 'returntocorp/semgrep-agent:v1'
    }

  }
  stages {
    stage('Semgrep') {
      steps {
        sh 'python -m semgrep-agent --publish-token $SEMGREP_APP_TOKEN'
      }
    }

  }
}