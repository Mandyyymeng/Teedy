pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                bat 'mvn -B -DskipTests clean package -Dmaven.wagon.http.ssl.insecure=true -Dmaven.wagon.http.ssl.allowall=true -Dmaven.wagon.http.ssl.ignore.validity.dates=true'
            }
        }
        stage('Doc'){
             steps {
                bat 'mvn javadoc:jar'
             }
             post {always {
                archiveArtifacts artifacts: '**\\target\\site\\apidocs\\**', fingerprint: true
                }
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

