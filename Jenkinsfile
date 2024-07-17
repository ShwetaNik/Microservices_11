pipeline {
    agent any

    stages {
        stage('Deploy to kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://ABD96E00870686F4F4E99ABA8CA304EF.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                }
            }
        }
            stage('verify deployment') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://ABD96E00870686F4F4E99ABA8CA304EF.gr7.ap-south-1.eks.amazonaws.com']]) {
                   sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}

