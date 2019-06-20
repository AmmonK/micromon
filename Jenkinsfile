void theProcess(folder,image) {  
  script {
  stage("permissions") {    
      dir(folder){
        sh "chmod 711 ./mvnw"
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