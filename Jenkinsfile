pipeline {
    agent any
   stages {     
    stage('Maven Install') { 
  steps {
       docker.image('maven:3.3.3-jdk-8').inside {
  sh 'mvn -B clean install'
}
       }
     }
   }
 }

