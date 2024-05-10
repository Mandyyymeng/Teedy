pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                bat 'mvn -B -DskipTests clean package'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
            post {
                always {
                    junit '**/target/surefire-reports/*.xml'
                }
            }
        }

        stage('pmd') {
            steps {
                bat 'mvn pmd:pmd'
            }
            post {
                always {
                    archiveArtifacts artifacts: '**\\target\\site\\**', fingerprint: true
                }
            }
        }

        stage('Generate Javadoc') {
            steps {
                bat 'mvn javadoc:jar'
            }
            post {
                always {
                    archiveArtifacts artifacts: '**\\target\\site\\apidocs\\**', fingerprint: true
                }
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: '**\\target\\**\\*.jar', fingerprint: true
            archiveArtifacts artifacts: '**\\target\\**\\*.war', fingerprint: true
        }
    }
}

