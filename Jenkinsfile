/* groovylint-disable FileEndsWithoutNewline, TrailingWhitespace, UnusedVariable, VariableName */
pipeline {
    agent {
        docker {
            label 'dockerserver'
            image 'maven:3-alpine'
            args '-v /root/.m2:/root/.m2'
            ENV JAVA_HOME=/usr/java/latest11
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
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
