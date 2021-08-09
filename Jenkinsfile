pipeline {
    environment {
        registry = "core.harbor.domain/harbor"
        registryCredential = 'admin'
    }
    
    agent any
    
    stages {
        stage("Checkout_branch") {
            steps {
                echo 'confirming branch...'
                git branch: 'main', credentialsId: 'rodrigoquijarro', url: 'https://github.com/rodrigoquijarro/test_helm.git'
            }
        }
        stage('Package Chart'){
            steps {
                
            }
        }

        stage('Push Chart') {
            when {
                expression { env.GIT_BRANCH ==~ /master/ }
            }
            steps {
                script {
                    docker.withRegistry( 'https://' + registry, dockerRegistryRWUserId) {
                        sh "docker push ${baseImageName}"
                    }
                }
            }
        }
    }    
}