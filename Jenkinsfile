<<<<<<< HEAD
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
        }
=======
pipeline{
  agent any
  
  stages {

    stage("build"){

      steps{
        echo 'Build the application'
>>>>>>> c74c7c2 (jenkins node update)
      }

    }
<<<<<<< HEAD
  post {
    always{
      echo 'Build status'
    }
  }
}
=======
    stage("Test"){

      steps{
        echo 'Test the application'
      }
      
    }

    stage("Deploy"){

      steps{
        echo 'Deploy the application'
      }
    
    }

  }

}
>>>>>>> c74c7c2 (jenkins node update)
