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
        stage('Automated UI Tests') {
          parallel{
            stage('Aquisitions Tests'){
          steps {
            sh '''echo "Executing automated acceptance tests"
sleep "5"
echo "Acceptance tests pass"'''
          }
            }
            stage('Partner & Rewards Tests'){
          steps {
            sh '''echo "Executing automated acceptance tests"
sleep "5"
echo "Acceptance tests pass"'''
          }
            }    
            stage('Online Claims Tests'){
          steps {
            sh '''echo "Executing automated acceptance tests"
sleep "5"
echo "Acceptance tests pass"'''
          }
            }                      
          }

        }
        stage('Performance Tests') {
          steps {
            sh '''echo "Executing performance tests"
sleep 5
echo "Performance tests complete"'''
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
    stage('Approve'){
      input {
        message "Is the release candidate approved for production?"
      }
      steps{
        sh '''echo "Deployment approved"'''
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