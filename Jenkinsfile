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
  post {
        failure {
          echo("**********************FAILED******************")
       mail bcc: 'ashwini.zanzad31@gmail.com', body: "<b>Example</b><br>Project: ${env.JOB_NAME} <br>Build Number: ${env.BUILD_NUMBER} <br> URL de build: ${env.BUILD_URL}", cc: '', charset: 'UTF-8', from: 'ashwini.zanzad31@gmail.com', mimeType: 'text/html', replyTo: 'ashwini.zanzad31@gmail.co.', subject: "ERROR CI: Project name -> ${env.JOB_NAME}", to: "ashwini.zanzad31@gmail.com";  

            //mailto: 'team@example.com', subject: 'The Pipeline failed :('
        }
    }
}
