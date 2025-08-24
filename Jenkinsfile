pipeline {
    agent any

    stages {
        stage('Deploy to kubernetes') {
            steps {
    withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'cluster1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://6D6519BE652ED0F90B3CDB1A82AD886D.gr7.ap-southeast-1.eks.amazonaws.com']]) {
            sh "kubectl apply -f deployment-service.yml" 
             sleep 60
              } 
            }
        }
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'cluster1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://6D6519BE652ED0F90B3CDB1A82AD886D.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                sh "kubectl get svc -n webapps"
               }
            }
        }
    }
}
