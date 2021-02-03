pipeline {
  agent {
    docker {
      image 'returntocorp/semgrep-agent:v1'
      args '-u root'
    }
  }

  environment {
    // secrets for Semgrep org ID and auth token
    SEMGREP_APP_TOKEN     = credentials('SEMGREP_APP_TOKEN')
    SEMGREP_DEPLOYMENT_ID = credentials('SEMGREP_DEPLOYMENT_ID')
    // environment variables for semgrep_agent (for findings / analytics page)
    SEMGREP_REPO_URL = "${GIT_URL}"
    SEMGREP_BRANCH = "${GIT_BRANCH}"
    SEMGREP_JOB_URL = "${BUILD_URL}"
    // https://stackoverflow.com/a/55500013/459909
    SEMGREP_REPO_NAME = env.GIT_URL.replaceFirst(/^.*\/([^\/]+?).git$/, '$1')
  }

  stages {
    stage('Semgrep_agent') {
      steps{
        sh 'python -m semgrep_agent --publish-token $SEMGREP_APP_TOKEN --publish-deployment $SEMGREP_DEPLOYMENT_ID'
      }
   }
  }
}
