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
       input(message: 'Deploy to PERF?', ok: 'Please proceed')
        sh 'echo Deploying PERF '
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
      steps {
        input(message: 'Deploy to production?', ok: 'Please proceed')
        sh 'echo Deploying production'
      }
    }
    stage('Report') {
      steps {
        sh 'echo Generating report'
      }
    }
  }
}
