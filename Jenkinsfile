pipeline {
  agent any
  stages {
    stage('Checkout code from Git') {
      steps {
        git(url: 'https://github.com/w-adisurya/portofolio', branch: 'main')
      }
    }

    stage('Check process') {
      parallel {
        stage('List current dir') {
          steps {
            sh 'ls -la'
          }
        }

        stage('Check script validity') {
          steps {
            sh 'node --check server.js'
          }
        }

      }
    }

    stage('Build') {
      steps {
        sh 'sudo docker build docker-app/ -t node-web-app'
      }
    }

  }
}