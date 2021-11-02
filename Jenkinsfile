pipeline {
    agent any
    stages {
        stage('Build Appln') {
            steps {
                build job: "Karun_DevOps_Build"
            }
        }
        stage('Deploy to Staging') {
             steps{
                 build job: "Karun_DevOps_Deploy_Staging"
             }
            }
        stage('Deploy to Production') {
             steps{
                 timeout(time:5, unit:'DAYS'){
                     input message:'Approve PRODUCTION Deployment?'
                 }
                 build job: "Karun_DevOps_Deploy_Production"
             }
        }
    }
}