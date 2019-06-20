def app

pipeline {
  agent any     
  stages {
    stage("build") {
      sh "cd AdminServer"
      sh "./mvnw install"
      app = docker.build("ammonking/admin-server")    
    }    
  }
}