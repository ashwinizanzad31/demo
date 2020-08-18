pipeline{
  agent any
  stages {
  stage ('Clean') {

steps{
    git credentialsId: 'Github', url: 'https://github.com/ashwinizanzad31/demo.git'

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
}
 }
  
   stage('Deploy'){
steps{
      echo('Deploying Code ') 
  }
}
  }
}
