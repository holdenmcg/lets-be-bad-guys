pipeline {
  agent none
  stages {
    stage('Test') {
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
        sh 'echo $SEMGREP_DEPLOYMENT_ID'
      }
    }

  }
  environment {
    SEMGREP_DEPLOYMENT_ID = 'credentials(\'SEMGREP_DEPLOYMENT_ID\')'
    SEMGREP_APP_TOKEN = 'credentials(\'SEMGREP_APP_TOKEN\')'
  }
}