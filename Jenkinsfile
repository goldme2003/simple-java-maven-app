pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'sudo mvn -B -DskipTests clean package'
            }
        }
        stage('Test') { 
            steps {
                sh 'sudo mvn test' 
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml' 
                }
            }
        }
    }
}


