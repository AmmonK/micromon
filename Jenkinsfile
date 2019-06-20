def app

pipeline {
  agent any     
  stages {
    stage("build") {
      steps{
        sh "cd AdminServer"
        sh "./mvnw install"
        app = docker.build("ammonking/admin-server")    
      }
    }    
  }
}