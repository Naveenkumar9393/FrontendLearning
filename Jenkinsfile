pipeline {
  agent any 
    stages{
      stage("frontend") {
        steps {
          echo 'Installing node js'
          nodeJs('Node'){
            sh 'yarn install'
          }
        }
      }
      stage("Backend") {
        steps {
          echo 'Installing gradle package ..'
          withGradle(){
            sh './gradlew -v'
          }
        }
      }
    }
}
