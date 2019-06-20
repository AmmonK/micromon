def app

pipeline {
  agent none
  stages {
    stage("build") {
      parallel {
        stage("AdminServer") {
          agent any
          stages {
            stage("test") {              
              steps {
                dir("AdminServer") {
                 sh "./mvnw test"
                }
              }
            }
          }
        }
         stage("DiscoveryServer") {
          agent any
          stages {
            stage("test") {
              steps {
                dir("DiscoveryServer") {
                  sh "./mvnw test"
                }
              }
            }
          }
        }
      }

      steps{
        sh "cd AdminServer"
        sh "./mvnw install"
        script {
          app = docker.build("ammonking/admin-server")    
        }
      }
    }    
  }
}