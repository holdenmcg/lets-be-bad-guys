pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo "PATH is: $PATH"
      }
    }

  }
  environment {
    PATH = "/usr/local/bin/:$PATH"
  }
}