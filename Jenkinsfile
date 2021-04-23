pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v /home/zen/.m2/mavenlocalRepos:/root/.m2'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -X -e -DskipTests clean package'
            }
        }
        stage('Test') { 
            steps {
                sh 'mvn test' 
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml' 
                }
            }
        }
    }
}


