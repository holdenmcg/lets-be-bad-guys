def scmInfo = scm

pipeline {
  agent {
    docker {
      image 'returntocorp/semgrep-agent:v1'
      args '-u root'
    }

  }

  environment {
    SEMGREP_APP_TOKEN     = credentials('SEMGREP_APP_TOKEN')
    SEMGREP_DEPLOYMENT_ID = credentials('SEMGREP_DEPLOYMENT_ID')
  }

  stages {
    stage('Prepare'){
      steps{
        echo scm.getUserRemoteConfigs()[0]
      }
    }

    stage('Semgrep_agent') {
      steps {
        sh 'python -m semgrep_agent --publish-token $SEMGREP_APP_TOKEN --publish-deployment $SEMGREP_DEPLOYMENT_ID'
     }
   }
  }
}

// $ SEMGREP_JOB_URL=https://example.com/me/myjob
// $ SEMGREP_REPO_URL=https://gitwebsite.com/myrepository
// $ SEMGREP_BRANCH=mybranch
// $ SEMGREP_REPO_NAME=myorg/myrepository