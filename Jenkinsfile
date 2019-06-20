def app1

def theProcess(folder,image) {
  dir(${folder}){
    sh "chmod 711 ./mvnw"
  }
}

pipeline {
  agent any
  stages {
    stage("sample") {
      steps {
        script {
          theProcess("AdminServer","admin-server")
        }
      }
    }
  }
}