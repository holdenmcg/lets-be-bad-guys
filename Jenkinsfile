pipeline {
  agent none
  stages {
    stage('Semgrep') {
      agent {
        docker {
          image 'returntocorp/semgrep-agent:v1'
        }

      }
      steps {
        sh 'python -c "which semgrep"'
      }
    }

  }
}