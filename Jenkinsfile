pipeline {
  environment {
    registry = 'registry.hub.docker.com'
    registryCredential = 'docker-hub'
    repository = 'pvnovarese/jenkins-simple'
  }
  agent any
  stages {
    stage('Checkout SCM') {
      steps {
        checkout scm
      }
    }
    stage('Build image and push to registry') {
      steps {
        sh 'docker --version'
        script {
          docker.withRegistry('https://' + registry, registryCredential) {
            def image = docker.build(repository)
            image.push()
          }
        }
      }
    }
  }
}
