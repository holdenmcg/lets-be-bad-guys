pipeline {
  agent { label 'docker' }
  environment {
    PATH = "/usr/local/bin/:$PATH"
  }
  stages {
    stage ('build') {
      steps {
        echo "PATH is: $PATH"
      }
    }
  }
}