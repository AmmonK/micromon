void theProcess(folder,image) {  
  def app
  script {
    stage("permissions") {    
      dir(folder){
        sh "chmod 711 ./mvnw"
      }    
    }
    stage("install") {
      dir(folder) {
        sh "./mvnw install"
      }
    }
    stage("build") {
      dir(folder) {
        app = docker.build("ammonking/"+image)
      }
    }
  }
}

pipeline {
  agent any
  stages {    
    stage ('automation') {
      steps {
        theProcess("AdminServer","admin-server")            
      }
    }       
  }
}