node { 
  stage("Clone repository") {
    /* clone the repository */
    checkout scm    
  }
}

stage "fix permissions"
parallel(
  AdminServer: { node {
    dir("AdminServer"){
      /* set maven wrapper permissions */
      sh 'pwd'
      sh "chmod 711 ./mvnw"
    }
  }},
    DiscoveryServer: { node {
    dir("DiscoveryServer"){
      sh 'pwd'
      /* set maven wrapper permissions */
      sh "chmod 711 ./mvnw"
    }
  }}
)