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
        sh 'python -m semgrep_agent --publish-deployment 56 --publish-token 613688c80f4787bf17e271587f2f782ef571784f95454c44aae112af79e05c5d'
      }
    }

  }
}