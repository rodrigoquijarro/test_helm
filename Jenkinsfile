pipeline {
  agent any
  stages {

    stage("Checkout_branch") {
        steps {
            echo 'confirming branch...'
            git branch: 'main', credentialsId: 'rodrigoquijarro', url: 'https://github.com/rodrigoquijarro/test_helm.git'
        }
    }
    stage('Run Helm') {
      steps {
      script {      
      container('helm') {
        sh "helm ls"
         }
        } 
      }
    }
  }
}