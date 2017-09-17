pipeline {
  agent any
  stages {
    stage('checkout code') {
      steps {
        sh 'echo "checking code out from github repo"'
      }
    }
    stage('build') {
      steps {
        sh 'echo "Running hybris build commands"'
      }
    }
    stage('build UI') {
      steps {
        sh 'echo "compile front ui code"'
      }
    }
    stage('unit test') {
      steps {
        sh 'echo "Running JUnit test"'
      }
    }
    stage('run bvt') {
      steps {
        sh 'echo "running selenium BVT script"'
      }
    }
    stage('deploy') {
      steps {
        sh 'echo "deploying ..."'
      }
    }
  }
}