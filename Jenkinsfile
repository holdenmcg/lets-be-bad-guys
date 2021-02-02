pipeline {
  agent {
    docker {
      image 'returntocorp/semgrep-agent:v1'
    }

  }
  stages {
    stage('Semgrep-agent') {
      agent {
        node {
          label 'master'
        }

      }
      environment {
        SEMGREP_DEPLOYMENT_ID = credentials('SEMGREP_DEPLOYMENT_ID')
        SEMGREP_APP_TOKEN = credentials('SEMGREP_APP_TOKEN')
      }
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