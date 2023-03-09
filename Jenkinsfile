pipeline {
    agent any
    environment {
        PROJECT_ID = 'redcliffelabs-cloud'
        CLUSTER_NAME = 'primary'
        LOCATION = 'asia-south2-a'
        CREDENTIALS_ID = 'jenkins'
    }
    stages {
        stage("Checkout code") {
            steps {
                checkout scm
            }
        }
        stage('Deploy to GKE') {
            steps{
                step([$class: 'KubernetesEngineBuilder', projectId: env.PROJECT_ID, clusterName: env.CLUSTER_NAME, location: env.LOCATION, manifestPattern: 'deployment.yaml', credentialsId: env.CREDENTIALS_ID, verifyDeployments: true])
            }
        }
    }    
}
