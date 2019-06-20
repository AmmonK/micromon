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
    stage("sample") {
      steps {       
          theProcess("AdminServer","admin-server")      
      }
    }
  }
}