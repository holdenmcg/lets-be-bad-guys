pipeline {
  agent any
  stages {
    stage('Semgrep') {
      parallel {
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

        stage('Stage2') {
          agent {
            node {
              label 'master'
            }

          }
          steps {
            sh 'python3 -m semgrep_agent --config "p/r2c-ci"'
          }
        }

      }
    }

  }
}