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
    SEMGREP_REPO_URL = scm.getUserRemoteConfigs()[0].getUrl()
  }

  stages {
    
  //   stage('Prepare'){
  //     steps{
  //       echo scm.getUserRemoteConfigs()[0].getUrl()
  //       echo scm.GIT_BRANCH
  //     }
  //   }

    stage('Semgrep_agent') {
      steps {
        echo $SEMGREP_REPO_URL
        sh 'python -m semgrep_agent --publish-token $SEMGREP_APP_TOKEN --publish-deployment $SEMGREP_DEPLOYMENT_ID'
     }
   }
  }
}

// $ SEMGREP_JOB_URL=https://example.com/me/myjob
// $ SEMGREP_REPO_URL=https://gitwebsite.com/myrepository
// $ SEMGREP_BRANCH=mybranch
// $ SEMGREP_REPO_NAME=myorg/myrepository
// From: https://stackoverflow.com/questions/39589360/how-to-access-git-branch-name-from-pipeline-job/48567672
// @RicardoStuven You need to authorize that method signature in the scripts console. – Oscar Bolaños Jul 8 '19 at 21:44
