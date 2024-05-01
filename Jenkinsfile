pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials:[[caCertificate: '', clusterName: 'EKS-2', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://6598A79B447F6B394149A89121B7C8F7.gr7.us-east-1.eks.amazonaws.com']]){ 
                 sh "kubectl apply -f deployment-service.yml"        
                
                }
            }
        }
    
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials:[[caCertificate: '', clusterName: 'EKS-2', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://6598A79B447F6B394149A89121B7C8F7.gr7.us-east-1.eks.amazonaws.com']]){ 
                sh "kubectl get svc -n webapps"
                }
            }
        }        
    }
}
