def app1
def app2
def app3
def app4

def theThing(folder,image) {
          stage(${folder}) {
          agent any
          stages {
            stage("build") {
              steps {
                dir(${folder}) {
                  sh "chmod 711 ./mvnw"
                  sh "./mvnw install"
                }
              }
            }
            stage("build docker") {
              steps {
                dir(${folder}) {
                  script {
                    app1 = docker.build("ammonking/"+${image})
                  }
                }
              }
            }
            stage("Push Image") {    
              steps {
                dir(${folder}){
                  script {
                    docker.withRegistry("https://registry.hub.docker.com", "docker-hub-credentials") {
                      app1.push("${env.BUILD_NUMBER}")
                      app1.push("latest")
                    }
                  }
                }                   
              }
            }
          }
        }
}

pipeline {
  agent none
  stages {
    stage("build") {
      parallel {
        stage {
          theThing("AdminServer","admin-server")
        }
        stage {
          theThing("DiscoveryServer","discovery-server")
        }
        
      }
    }    
  }
}