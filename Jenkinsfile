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
    SEMGREP_REPO_URL = "${GIT_URL}"
    SEMGREP_BRANCH = "${GIT_BRANCH}"
    SEMGREP_JOB_URL = "${BUILD_URL}"
    // https://stackoverflow.com/a/55500013/459909
    SEMGREP_REPO_NAME = env.GIT_URL.replaceFirst(/^.*\/([^\/]+?).git$/, '$1')
   

  }

  stages {

    // stage('Prepare'){
    //   steps{
    //     script{
    //       SEMGREP_BRANCH =  scm.GIT_BRANCH
    //     }
    //   }
    // }

    stage('Semgrep_agent') {
      steps{
        sh '''
          echo $SEMGREP_BRANCH; 
          echo $SEMGREP_REPO_URL; 
          echo $SEMGREP_REPO_NAME; 
          echo $SEMGREP_JOB_URL;
          python -m semgrep_agent --publish-token $SEMGREP_APP_TOKEN --publish-deployment $SEMGREP_DEPLOYMENT_ID
        '''
      }
   }
  }
}



    // SEMGREP_REPO_URL = scm.getUserRemoteConfigs()[0].getUrl()