def app

pipeline {
  agent any     
  stages {
    stage("build") {
      steps{
        sh "cd AdminServer"
        sh "./mvnw install"
        script {
          app = docker.build("ammonking/admin-server")    
        }
      }
    }    
  }
}