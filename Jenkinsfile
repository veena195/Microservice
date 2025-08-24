pipeline {
    agent any

    stages {
        stage('Deploy to kubernets') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://95C13F48FAA2B0F398FD1BEF3EB21553.gr7.ap-south-1.eks.amazonaws.com']]) {
                  sh "kubectl apply -f deployment-service.yml"
                  sleep 60
                }
            }
        }
         stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://95C13F48FAA2B0F398FD1BEF3EB21553.gr7.ap-south-1.eks.amazonaws.com']]) {
                sh "kubectl get svc -n webapps"
               }
            }
        }
    }
}
