pipeline {
    agent any
    stages {
        
        stage('K8s') {
            steps {
                bat 'kubectl set image deployments/hello-node hello-node-5dd5dcf7b4=myteedy05:latest'
            }
         }
    }

    post {
        always {
            archiveArtifacts artifacts: '**\\target\\site\\**', fingerprint: true
            archiveArtifacts artifacts: '**\\target\\**\\*.jar', fingerprint: true
            archiveArtifacts artifacts: '**\\target\\**\\*.war', fingerprint: true
        }
    }

}

