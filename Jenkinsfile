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
            cobertura(coberturaReportFile: 'client/coverage/cobertura-coverage.xml', sourceEncoding: 'ASCII', enableNewApi: true)
            junit 'client/*.xml'
          }
        }

      }
    }

    stage('error') {
      steps {
        echo 'Space'
      }
    }

    stage('Back End') {
      parallel {
        stage('Back End') {
          steps {
            echo 'Back End'
          }
        }

        stage('Maven Install') {
          steps {
            sh 'sudo apt-get install maven -y'
          }
        }

        stage('Maven Build') {
          steps {
            sh 'mvn clean install'
          }
        }

        stage('Maven Coverage and Test report') {
          steps {
            sh 'mvn clean install'
            cobertura(enableNewApi: true, sourceEncoding: 'ASCII', coberturaReportFile: 'target/site/cobertura/coverage.xml', lineCoverageTargets: '80, 0, 0', methodCoverageTargets: '80, 0, 0', conditionalCoverageTargets: '70, 0, 0')
            junit '**/surefire-reports/*.xml'
          }
        }

      }
    }

  }
}