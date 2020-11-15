pipeline {
  agent any
  stages {
    stage('Semgrep') {
      agent {
        docker {
          image 'returntocorp/semgrep-agent:v1'
        }

      }
      steps {
        sh 'python -m semgrep_agent --publish-deployment $SEMGREP_DEPLOYMENT_ID --publish-token $SEMGREP_APP_TOKEN'
      }
    }

  }
}