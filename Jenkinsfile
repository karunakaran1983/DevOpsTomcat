pipeline {
    agent any
    stages {
        stage('Build Appln') {
            steps {
                echo "Clean & Package using Maven"
                sh 'mvn clean package'
            }
            post {
                success {
                    echo "Archive the Artifacts"
                    archiveArtifacts artifacts: '**/*.war'
                }
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