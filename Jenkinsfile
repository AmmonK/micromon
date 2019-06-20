def app1

def theProcess(folder,image) {
  echo folder
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