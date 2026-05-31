pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'eks-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://813F4B992EF7723320A61448255B5765.gr7.ap-south-2.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'eks-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://813F4B992EF7723320A61448255B5765.gr7.ap-south-2.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
