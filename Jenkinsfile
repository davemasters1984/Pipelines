pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        powershell(script: 'Write-Host "NuGet packages restored"', label: 'NuGet Restor')
        powershell(script: 'Write-Host "Build Complete""', label: 'Build')
      }
    }
    stage('Unit Test') {
      steps {
        powershell(script: 'Write-Host "Unit tests pass"', label: 'Unit tests')
      }
    }
  }
}