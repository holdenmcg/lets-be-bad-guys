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
        sh 'python -c "import os; os.system(\\"uname \\-a \\")'
      }
    }

  }
}