pipeline {
  agent any {    
    def app
    stage("build") {
      sh "cd AdminServer"
      sh "./mvnw install"
      app = docker.build("ammonking/admin-server")    
    }    
  }
}