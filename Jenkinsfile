pipeline {
  agent any
  stages {
    stage('Checkout code') {
      steps {
        git(url: 'https://github.com/w-adisurya/portofolio', branch: 'main')
      }
    }

    stage('Log check dir') {
      parallel {
        stage('Log check dir') {
          steps {
            sh 'ls -la'
          }
        }

        stage('Front End Unit Tests') {
          steps {
            sh 'node --check server.js'
          }
        }

      }
    }

  }
}