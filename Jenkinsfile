pipeline {
  agent any
  stages {
    stage('Semgrep python') {
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
        sh 'python3 -m semgrep_agent --publish-deployment $SEMGREP_DEPLOYMENT_ID --publish-token $SEMGREP_APP_TOKEN'
      }
    }

  }
}