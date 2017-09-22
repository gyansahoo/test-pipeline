pipeline {
  agent any
  stages {
    stage('checkout code') {
      steps {
         sh 'echo "checking code out from github repo"'
        }
    }
    stage('Static Analysis') {
      when {
        branch 'master'
      }
      steps {
        sh '''echo "Static Analysis ...."

echo "Code coverage checks, PMD, FindBugs and etc."
'''
      }
    }
    stage('build backend') {
      steps {
        sh '''echo "Running hybris build commands"
echo "ant customize clean all"'''
      }
    }
    stage('build front-end') {
      steps {
        sh '''echo "compile front ui code"
echo "npm install"
echo "npm run prod or vue.dev"'''
        sh 'node --version'
      }
    }
    stage('Deploy QA') {
      steps {
        sh 'echo "deploying on QA ...."'
      }
    }
    stage('Deploy Perf') {
      steps {
        parallel(
          "Deploy Perf": {
            input(message: 'Deploy to PERF?', ok: 'Please proceed')
            sh 'echo Deploying PERF '

          },
          "Node-1": {
            sh 'echo deploying perf node-1'

          },
          "Node-2": {
            sh 'echo deploying perf node-2'

          }
        )
      }
    }
    stage('Backend Test') {
      steps {
        parallel(
          "Unit": {
            sh 'echo Unit test'

          },
          "Performance": {
            sh '''echo Performance test
           echo "Blaze meter load testing"'''

          }
        )
      }
    }
    stage('BVT - Selenium') {
      steps {
        sh 'echo "running selenium BVT script"'
      }
    }
    stage('Deploy production') {
    when {
      branch 'master'
    }
      steps {
        parallel(
          "Deploy production": {
            input(message: 'Deploy to production?', ok: 'Please proceed')
            sh 'echo Deploying production'

          },
          "Node-1": {
            sh 'echo deploying on node-1'

          },
          "Node-2": {
            sh 'echo deploying node-2'

          },
          "Node-3": {
            sh 'echo deploying node-3'

          }
        )
      }
    }
    stage('Report') {
      steps {
        sh 'echo Generating report'
      }
    }
  }
}
