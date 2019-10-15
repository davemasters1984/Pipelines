pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'echo "Restoring NuGet Packages"'
      }
    }
    stage('Unit Test') {
      steps {
        sh 'echo "Executing unit tests"'
      }
    }
  }
}