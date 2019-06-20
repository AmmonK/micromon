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
              dir("AdminServer") {
                steps {
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
              dir("DiscoveryServer") {
                steps {
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