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
            sh 'cd client && npm install'
          }
        }

        stage('Npm Code Coverage  & Test Report') {
          steps {
            sh 'cd client && npm install && npm i -D jest-junit-reporter && npm test -- --coverage --watchAll=false'
          }
        }

        stage('Coverage Report') {
          steps {
            cobertura(enableNewApi: true, sourceEncoding: 'ASCII', coberturaReportFile: '/home/ubuntu/.jenkins/workspace/React-pipeline_dev/client/coverage/cobertura-coverage.xml')
          }
        }

      }
    }

  }
}