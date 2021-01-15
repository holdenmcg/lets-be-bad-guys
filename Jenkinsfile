pipeline {
  agent {
    docker {
      image 'returntocorp/semgrep-agent:v1'
    }

  }
  stages {
    stage('Semgrep python') {
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
        sh '''echo \'Running semgrep...\'
/usr/local/bin/docker run --rm -v "${PWD}:/src" returntocorp/semgrep --config=https://semgrep.dev/p/r2c-CI'''
      }
    }

  }
}