pipeline {
  agent {
    docker {
      image 'returntocorp/semgrep-agent:v1'
      args '-u root'
    }
  }

  stages {
    stage('Semgrep-agent') {
      environment {
        SEMGREP_APP_TOKEN     = credentials('SEMGREP_APP_TOKEN')
        SEMGREP_DEPLOYMENT_ID = credentials('SEMGREP_DEPLOYMENT_ID')
    }
      steps {
          sh 'python -m semgrep-agent --publish-token $SEMGREP_APP_TOKEN'
      }
    }
  }
}  
