def app1
def app2
def app3
def app4

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
            stage("build") {
              steps {
                dir("AdminServer") {
                  sh "./mvnw install"
                }
              }
            }
            stage("build docker") {
              steps {
                dir("AdminServer") {
                  script {
                    app1 = docker.build("ammonking/admin-server")
                  }
                }
              }
            }
            stage("Push Image") {    
              steps {
                dir("AdminServer"){
                  script {
                    docker.withRegistry("https://registry.hub.docker.com", "docker-hub-credentials") {
                      app.push("${env.BUILD_NUMBER}")
                      app.push("latest")
                    }
                  }
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