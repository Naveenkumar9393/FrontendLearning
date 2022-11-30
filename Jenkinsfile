pipeline {
  agent any 
    stages{
      stage("frontend") {
        steps {
          echo 'Installing node js'
          nodejs('Node-19'){
            sh 'yarn install'
          }
        }
      }
      stage("Backend") {
        steps {
          echo 'Installing gradle package ..'
          withGradle(){
            echo 'Gradle version is ..'gradle --version
          }
        }
      }
    }
}
