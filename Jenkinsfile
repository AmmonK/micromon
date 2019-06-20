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
                  sh "chmod 711 ./mvnw"
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
                  sh "chmod 711 ./mvnw"
                  sh "./mvnw test"
                }
              }
            }
          }
        }
      }
    }    
  }
}