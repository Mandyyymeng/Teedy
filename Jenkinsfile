pipeline {
    agent any
    stages {
        
        stage('K8s') {
            steps {
                bat 'kubectl set image deployments/hello-node docs=myteedy05:latest'
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

