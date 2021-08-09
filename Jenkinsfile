String registry = 'docker.soramitsu.co.jp'
String baseChartName = 'docker.soramitsu.co.jp/harbor/projects/11/helm-charts:latest'

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
                 sh helm package 
                 sh push_helm 
            }
        }

        stage('Push Chart') {
            when {
                expression { env.GIT_BRANCH ==~ /master/ }
            }
            steps {
                script {
                    docker.withRegistry( 'https://' + registry, dockerRegistryRWUserId) {
                        sh "helm push ${baseChartName}"
                    }
                }
            }
        }
    }    
}