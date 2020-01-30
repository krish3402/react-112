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
              stage ('Node & npm Install') {
                steps {
                  sh label: '', script: 'sudo apt-get install nodejs -y'
                  sh label: '', script: 'sudo apt-get install npm -y'

                }
              }
            }

          }
        }

      }
    }

    stage('Back End') {
      agent any
      steps {
        sh 'Back End'
      }
    }

  }
}