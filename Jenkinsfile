pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '''echo "Restoring NuGet Packages"
sleep 5
echo "NuGet packages restored"'''
        sh '''echo "Building"
sleep 5
echo "Build Successful"'''
      }
    }
    stage('Unit Test') {
      parallel {
        stage('Unit Test') {
          steps {
            sh '''echo "Executing unit tests"
sleep 5 
echo "Units tests pass"'''
          }
        }
        stage('Code Analysis') {
          steps {
            sh '''echo "Running Code Analysis"
sleep 10
echo "Code Analysis Passed"'''
          }
        }
      }
    }
    stage('Deploy to Staging') {
      steps {
        sh '''echo "Deploying to test environment"
sleep 5
echo "Deployment complete"
'''
      }
    }
    stage('Acceptance Tests') {
      parallel {
        stage('Aquisition UI Tests') {
          steps {
            sh '''echo "Executing Acquisition automated UI tests"
sleep "5"
echo "Acceptance tests pass"'''
          }
        }
        stage('Partner & Rewards UI Tests') {
          steps {
            sh '''echo "Executing Partner & Rewards automated UI tests"
sleep 5
echo "Tests complete"'''
          }
        }
        stage('Online Claims UI Tests') {
          steps {
            sh '''echo "Executing Online Claims tests"
sleep 5
echo "Tests complete"'''
          }
        }
        stage('Performance Tests') {
          steps {
            sh '''echo "Executing performance tests"
sleep 10 
echo "Tests complete"'''
          }
        }
      }
    }
    stage('Deploy to Prod') {
      steps {
        sh '''echo "Deploying to dormant production environment"
sleep 5
echo "Production deployment complete"'''
      }
    }
    stage('Approve') {
      input {
        message 'Is the release candidate approved for production?'
      }
      steps {
        sh 'echo "Deployment approved"'
      }
    }
    stage('Switch DNS for go-live') {
      steps {
        sh '''echo "Swapping DNS for production"
sleep 2
echo "DNS swapped - Green environment now live"'''
      }
    }
  }
}