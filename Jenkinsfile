pipeline {
    agent any
    stages {
        stage('Build Appln'){
            steps{
                echo "Clean & Package using Maven"
                sh 'mvn clean package'
            }
            post {
                success {
                    echo "Archive the Artifacts"
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
            stage('Deploy to Staging') {
                build job: "Karun_DevOps_Deploy_Staging"
            }
            stage('Deploy to Production') {
                build job: "Karun_DevOps_Deploy_Production"
            }
        }
    }
}