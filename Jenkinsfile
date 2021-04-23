pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v /root/.m2:/home/zen/.m2/mavenlocalRepos'
        }
    }
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


