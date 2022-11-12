pipeline {
  agent any
  stages {
    stage('Checkout code') {
      steps {
        git(url: 'https://github.com/w-adisurya/portofolio', branch: 'main')
      }
    }

    stage('Log check dir') {
      steps {
        sh 'ls -la'
      }
    }

  }
}