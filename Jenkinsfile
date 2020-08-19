pipeline {
    agent any
   stages {     
    stage('Maven Install') { 
  steps {
       sh 'docker pull maven:3.5.0'
       sh 'mvn clean install'
       }
     }
   }
 }

