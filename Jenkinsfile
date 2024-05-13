pipeline {
    agent any
    stages {
        
        stage('K8s') {
            steps {
                bat 'kubectl set image deployments/hello-node docs=mandy-zhang/myteedy05:latest'
            }
         }
    }

}

