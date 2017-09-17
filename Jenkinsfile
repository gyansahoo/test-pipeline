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
	sh 'node --version'
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
	input message: 'Deploy to production',
	ok: 'Please proceed'
        sh 'echo "deploying ...."'
      }
    }
  }
}
