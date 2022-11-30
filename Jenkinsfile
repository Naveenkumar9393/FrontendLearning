// CODE_CHANGES = getGitChanges()
// when {
// expression {
// BRANCH_NAME == 'dev' || CODE_CHANGES == true
// }
pipeline{
  agent any
  parmeters {
    String(name: 'VERSION' , 
    choices :['1.1.0' , '1.2.0'],
    booleanParam(name: 'executeTests'),
    dafaultValue: true,
    description: 'version to deploy on prod')
  }
  tools {
    maven 'Maven'
  }
  environment {
    NEW_VERSION ='1.1.0'
    SERVER_CREDENTIALS = credentials('server-credentials')
  }
  stages {

    stage("build"){
      steps{
        echo 'Build the application'
        echo  "Building version ${NEW_VERSION}"
        sh "mvn install"
      }

    }
    stage("Test") {
      when {
        expression {
          BRANCH_NAME == 'dev' || BRANCH_NAME == 'master'
          params.executeTests='True'
        }
      }
      steps{
        echo 'Test the application'
      }
    }

    stage("Deploy"){
      steps{
        echo 'Deploy the application'
        echo "Deploying with ${SERVER_CREDENTIALS}"
        sh "${SERVER_CREDENTIALS}"
        echo 'Stage level creds'
        withCredentials([
          usernamePassword(credentials : 'server-credentials',
          usernameVariable : USER ,
          passwordVariable : PWD)
        ]){
          sh "some script ${USER} S{PWD}"
        }
      }
    
    }
  }
  post {
    always {
       // This script executes always 
    }
    success {
      echo 'verify success is printed in post command'
    }
    failure {
      echo 'verify Failure is printed in post command'
    }
  }
}
