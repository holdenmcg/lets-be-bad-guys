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
        sh '''withCredentials([string(credentialsId: \'SEMGREP_APP_TOKEN\', variable: \'SEMGREP_APP_TOKEN\')]){
python -m semgrep-agent --publish-token $SEMGREP_APP_TOKEN
}'''
        }
      }

    }
    environment {
      SEMGREP_DEPLOYMENT_ID = 'credentials(\'SEMGREP_DEPLOYMENT_ID\')'
      SEMGREP_APP_TOKEN = 'credentials(\'SEMGREP_APP_TOKEN\')'
    }
  }