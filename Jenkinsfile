pipeline {
  agent {
    docker {
      image 'returntocorp/semgrep-agent:v1'
      args '-u root'
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