pipeline {
  agent any
  stages {

    stage("Checkout_branch") {
        steps {
            echo 'confirming branch...'
            git branch: 'main', credentialsId: 'rodrigoquijarro', url: 'https://github.com/rodrigoquijarro/test_helm.git'
        }
    }
    
    stage("Make_pack") {
        steps {
            echo 'Packaging updated helm... '
        }
    }
    stage("Upload_to_Harbor"){
        steps {
            echo 'Uploading to Harbor...'
        }
    }
  }
}