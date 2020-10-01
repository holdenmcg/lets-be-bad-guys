pipeline {
  agent any
  stages {
    stage('Semgrep') {
      steps {
        sh '''echo \'Running semgrep...\'
semgrep --config https://semgrep.live/c/p/r2c-ci '''
      }
    }

  }
}