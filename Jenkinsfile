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
        sh 'python -m semgrep_agent --config "p/r2c-ci"'
      }
    }

  }
}