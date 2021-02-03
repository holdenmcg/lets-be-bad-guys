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

  def scmVars

  

  stages {
    stage('Clone source code') {
        scmVars = checkout scm
        // scmVars contains the following values
        // GIT_BRANCH=origin/mybranch
        // GIT_COMMIT=fc8279a107ebaf806f2e310fce15a7a54238eb71
        // GIT_PREVIOUS_COMMIT=6f2e319a1fc82707ebaf800fce15a7a54238eb71
        // GIT_PREVIOUS_SUCCESSFUL_COMMIT=310fce159a1fc82707ebaf806f2ea7a54238eb71
        // GIT_URL=https://stash.someworkplace.com/scm/poc/api-sample.git
    }
    stage('test scope'){
      echo scmVars.GIT_BRANCH
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