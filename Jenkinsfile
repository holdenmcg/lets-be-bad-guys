pipeline {
  agent {
    docker {
      image 'returntocorp/semgrep-agent:v1'
      args '-u root'
    }

  }
  stages {
    stage('Semgrep_agent') {
      steps {
        sh 'python -m semgrep_agent --publish-token $SEMGREP_APP_TOKEN'
      }
    }

  }
}