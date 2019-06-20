void theProcess(folder,image) {  
  stage("permissions") {
    steps {
      dir(folder){
        sh "chmod 711 ./mvnw"
      }
    }
  }
}

pipeline {
  agent any
  stages {     
      theProcess("AdminServer","admin-server")            
  }
}