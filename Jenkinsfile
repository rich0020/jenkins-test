pipeline {
    agent any
    environment {
        TF_VAR_gcp_project = "qwiklabs-gcp-02-91ec99e82d94"
        TF_VAR_bucket = "tf-remote-state-student_00_9c8ad21227f6-32720-19984"
    }
    stages {
        stage('Terraform Init') {
            steps {
                withCredentials([file(credentialsId: 'gcp-svc-acct', variable: 'GOOGLE_CLOUD_KEYFILE_JSON')]) {
                    sh '''
                    export GOOGLE_APPLICATION_CREDENTIALS=$GOOGLE_CLOUD_KEYFILE_JSON
                    terraform init
                    '''
                }
            }
        }
        stage('Terraform Plan') {
            steps {
                withCredentials([file(credentialsId: 'gcp-svc-acct', variable: 'GOOGLE_CLOUD_KEYFILE_JSON')]) {
                    sh '''
                    export GOOGLE_APPLICATION_CREDENTIALS=$GOOGLE_CLOUD_KEYFILE_JSON
                    terraform plan
                    '''
                }
            }
        }
        stage('Terraform Apply') {
            steps {
                withCredentials([file(credentialsId: 'gcp-svc-acct', variable: 'GOOGLE_CLOUD_KEYFILE_JSON')]) {
                    sh '''
                    export GOOGLE_APPLICATION_CREDENTIALS=$GOOGLE_CLOUD_KEYFILE_JSON
                    terraform apply -auto-approve
                    '''
                }
            }
        }
    }
}
