pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                bat 'mvn -B -DskipTests clean package'
            }
        }

stage('Doc'){
             steps {
                bat 'mvn javadoc:javadoc --fail-never'
             }
        }

        stage('pmd') {
            steps {
                bat 'mvn pmd:pmd'
            }
        }

        stage('test report'){
           steps {
                        bat 'mvn test'
                    }
                    post {
                        always {
                            junit '**\\target\\surefire-reports\\*.xml'
                        }
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
   
