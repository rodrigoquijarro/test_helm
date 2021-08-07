pipeline {
  agent any
  stages {

    stage('Checkout') {
        steps {
            git branch: 'main', credentialsId: 'rodrigoquijarro', url: 'https://github.com/rodrigoquijarro/test_helm.git'
        }
    }
  }
}