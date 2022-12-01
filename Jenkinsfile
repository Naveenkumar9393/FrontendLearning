// // CODE_CHANGES = getGitChanges()
// // when {
// // expression {
// // BRANCH_NAME == 'dev' || CODE_CHANGES == true
// // }
// // environment {
// // NEW_VERSION ='1.1.0'
// // SERVER_CREDENTIALS = credentials('server-credentials')
// // }
// pipeline{
//   agent any
//   parmeters {
//     choice(name: 'VERSION', choices: ['1.1.0', '1.2.0','1.3.0'],description: '')
//     booleanParam(name: 'executeTests',dafaultValue: true,description: '')
//   }
//   tools {
//     maven 'Maven'
//   }
//   environment {
//     NEW_VERSION ='1.1.0'
//     SERVER_CREDENTIALS = credentials('server-credentials')
//   }
//   stages {

//     stage("build"){
//       steps{
//         echo 'Build the application'
//         echo  "Building version ${NEW_VERSION}"
//         // sh "mvn install"
//       }

//     }
//     stage("Test") {
//       when {
//         expression {
//           BRANCH_NAME == 'dev' || BRANCH_NAME == 'master'
//           params.executeTests='True'
//         }
//       }
//       steps{
//         echo 'Test the application'
//       }
//     }

//     stage("Deploy"){
//       steps{
//         echo 'Deploy the application'
//         echo "Deploying with ${SERVER_CREDENTIALS}"
//         sh "${SERVER_CREDENTIALS}"
//         echo 'Stage level creds'
//         withCredentials([
//           usernamePassword(credentials : 'server-credentials',
//           usernameVariable : USER ,
//           passwordVariable : PWD)
//         ]){
//           sh "some script ${USER} S{PWD}"
//         }
//       }
    
//     }
//   }
//   post {
//     //always {
//        // This script executes always 
//     //}
//     success {
//       echo 'verify success is printed in post command'
//     }
//     failure {
//       echo 'verify Failure is printed in post command'
//     }
//   }
// }
pipeline{
  agent any
  parameters{
    choice(name: 'VERSION', choices: ['1.1.0', '1.2.0','1.3.0'])
    // booleanParam(name: 'executeTests',dafaultValue: true)
  }
  stages{
    stage("build"){
      steps{
        echo 'building application ...'
      }
    }
    stage("test"){
      steps{
        echo 'Testing application ...'
      }
    }
    stage("deploy"){
      steps{
        echo 'Deploying application ...'
        echo "Deployed version ${params.VERSION)"
        sh "mvn clean install"
      }
    }
  }
}
