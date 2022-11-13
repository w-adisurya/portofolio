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
            sh 'ls -la && whoami'
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
        sh 'docker build -f docker-app/Dockerfile . -t node-app:latest'
      }
    }

    stage('Login to dockerhub') {
      environment {
        DOCKERHUB_USER = 'wadisurya'
        DOCKERHUB_PASS = 'Docker1!'
      }
      steps {
        sh 'docker login -u $DOCKERHUB_USER -p $DOCKERHUB_PASS'
      }
    }

    stage('Docker push') {
      steps {
        sh 'docker push wadisurya/portofolio:latest'
      }
    }

  }
}