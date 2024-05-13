pipeline {
    agent any
    stages {
        
        stage('K8s') {
            steps {
                bat 'kubectl set image deployments/hello-node docs=myteedy05:latest'
            }
         }
    }

}

