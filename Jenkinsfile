pipeline {
  agent {
    docker {
      image 'returntocorp/semgrep-agent:v1'
      args '-u root'
    }

  }
  stages {
    stage('Semgrep-agent') {
      steps {
        sh 'python -m semgrep_agent --publish-deployment $SEMGREP_DEPLOYMENT_ID --publish-token $SEMGREP_APP_TOKEN'
      }
    }

  }
  environment {
    SEMGREP_DEPLOYMENT_ID = 'credentials(\'SEMGREP_DEPLOYMENT_ID\')'
    SEMGREP_APP_TOKEN = 'credentials(\'SEMGREP_APP_TOKEN\')'
  }
}