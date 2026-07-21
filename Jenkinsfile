pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-CLOUD', contextName: '', credentialsId: 'snoopy', namespace: 'webapps', serverUrl: 'https://38BA494B40197FD0D5D88E446F06A46B.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-CLOUD', contextName: '', credentialsId: 'snoopy', namespace: 'webapps', serverUrl: 'https://38BA494B40197FD0D5D88E446F06A46B.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
