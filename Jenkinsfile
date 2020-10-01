pipeline {
  agent any
  stages {
    stage('Semgrep') {
      steps {
        sh '''echo \'Running semgrep...\'
/usr/local/bin/semgrep --config https://semgrep.live/c/p/r2c-ci '''
      }
    }

  }
}