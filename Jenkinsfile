pipeline {
  agent {
    docker {
      // Make sure you have the latest semgrep-agent
      // This file is tested with semgrep 0.39.1 on Python 3.9.1
      // For the latest agent, use 'docker pull returntocorp/semgrep-agent:v1'
      image 'returntocorp/semgrep-agent:v1'
      // By default, Jenkins doesn't run docker in root mode
      // So you have to specify the root user
      args '-u root'
    }
  }

  environment {
    // secrets for Semgrep org ID and auth token
    // this requires the Jenkisn credentials Plugin
    SEMGREP_APP_TOKEN     = credentials('SEMGREP_APP_TOKEN')
    SEMGREP_DEPLOYMENT_ID = credentials('SEMGREP_DEPLOYMENT_ID')

    // environment variables for semgrep_agent (for findings / analytics page)
    // remove .git at the end
    SEMGREP_REPO_URL = env.GIT_URL.replaceFirst(/^(.*).git$/,'$1')
    SEMGREP_BRANCH = "${GIT_BRANCH}"
    SEMGREP_JOB_URL = "${BUILD_URL}"
    // remove SCM URL + .git at the end
    SEMGREP_REPO_NAME = env.GIT_URL.replaceFirst(/^https:\/\/github.com\/(.*).git$/, '$1')
  }

  stages {
    stage('Semgrep_agent') {
      steps{
        sh 'python -m semgrep_agent --config=r/r2c-ci'
      }
   }
  }
}
