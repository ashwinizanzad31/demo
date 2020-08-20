pipeline{
  agent any
  parameters {
        string(name: 'Greeting', defaultValue: 'Hello', description: 'How should I greet the world?')
    }
  stages {
  stage ('Clean') {

steps{
    withMaven(
        maven: 'maven-3') {
       echo "${params.Greeting} World!"
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
  build 'MyDotNetPipeline'
  echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
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
