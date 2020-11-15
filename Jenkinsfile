pipeline {
  agent any
  stages {
    stage('Semgrep') {
      agent {
        docker {
          image 'returntocorp/semgrep-agent:v1'
        }

      }
      steps {
        sh 'semgrep --version'
      }
    }

  }
}