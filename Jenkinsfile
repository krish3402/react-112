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
            script {
              sudo apt-get install nodejs -y
            }

            sh 'sudo apt-get install nodejs -y'
          }
        }

      }
    }

  }
}