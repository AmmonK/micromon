def app

pipeline {
  agent any     
    
    stage("build") {
      sh "cd AdminServer"
      sh "./mvnw install"
      app = docker.build("ammonking/admin-server")    
    }    
  
}