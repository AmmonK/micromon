def app1

void theProcess(folder,image) {
  dir(folder){
    sh "chmod 711 ./mvnw"
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