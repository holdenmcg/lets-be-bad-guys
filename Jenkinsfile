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

  node {
    def scmVars = checkout scm
    echo 'scm : the commit id is ' +scmVars.GIT_COMMIT
    echo 'scm : the commit branch  is ' +scmVars.GIT_BRANCH
    echo 'scm : the previous commit id is ' +scmVars.GIT_PREVIOUS_COMMIT
    def commitEmail = sh(returnStdout: true, script: "git --no-pager show -sformat=\'%ae\'")
    echo " the commiter email is'${commitEmail}'"
    def commitName = sh(returnStdout: true, script: "git --no-pager show -s format=\'%an\'")
    echo " the commiter name is'${commitName}'"
  }
  
  stages {
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