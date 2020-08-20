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
      sh "mvn test"

    } 
  }
}
  
   stage('Test'){
steps{
 echo('Testing Code ')
 echo('Building other pipeline') 
   sh 'make check || true' 
  build 'MyDotNetPipeline'
}
 }
  
   stage('Deploy'){
steps{
      echo('Deploying Code ') 
  }
}
  }
}
