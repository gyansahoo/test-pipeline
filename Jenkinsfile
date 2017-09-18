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
        branch 'master1'
      }
      steps {
        sh 'echo "Static Analysis ...."'
      }
    }
    stage('build backend') {
      steps {
        sh 'echo "Running hybris build commands"'
      }
    }
    stage('build front-end') {
      steps {
        sh 'echo "compile front ui code"'
        sh 'node --version'
      }
    }
    stage('Backend Test') {
      steps {
        parallel(
          "Unit": {
            sh 'echo Unit test'
            
          },
          "Performance": {
            sh 'echo Performance test'
            
          }
        )
      }
    }
    stage('BVT - Selenium') {
      steps {
        sh 'echo "running selenium BVT script"'
      }
    }
    stage('Deploy QA') {
      steps {
        sh 'echo "deploying on QA ...."'
      }
    }
    stage('Deploy Perf') {
      steps {
        sh 'echo Deploying PERF '
      }
    }
    stage('Deploy production') {
      steps {
        input(message: 'Deploy to production', ok: 'Please proceed')
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