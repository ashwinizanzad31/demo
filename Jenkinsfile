pipeline{
  agent any
  stages {
  stage ('Clean') {

steps{
    withMaven(
        maven: 'maven-3') {
      sh "mvn clean"

    } 
}
  }
  stage('Build'){
steps{
      withMaven(
        maven: 'maven-3') {
      //sh "mvn test"
        echo 'Build phase'

    } 
  }
}
  
   stage('Test'){
steps{
 echo('Testing Code ')
 //echo('Building other pipeline') 
  //build 'MyDotNetPipeline'
}
 }
  
   stage('Deploy'){
      when {
              expression {
                currentBuild.result == null || currentBuild.result == 'SUCCESS' 
              }
            }
steps{
      echo('Deploying Code ') 
  }
}
  }
}
