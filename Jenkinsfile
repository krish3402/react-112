pipeline {
  agent any
  stages {
    stage('Front End') {
      parallel {
        stage('Front End') {
          steps {
            echo 'Front End'
          }
        }

        stage('Node & Npm Install') {
          steps {
            sh 'sudo apt-get install nodejs -y && sudo apt-get install npm -y'
          }
        }

        stage('Npm Packages install') {
          steps {
            sh 'cd client && npm install && npm i -D jest-junit-reporter'
          }
        }

        stage('Npm Code Coverage & Test Result') {
          steps {
            sh 'npm test -- --coverage --watchAll=false'
          }
        }

      }
    }

  }
}