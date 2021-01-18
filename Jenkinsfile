/* groovylint-disable CompileStatic, FileEndsWithoutNewline, TrailingWhitespace */
pipeline {
    agent { label 'rhel7' }
    stages {
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package' 
            }
        }        
        
        stage('Test') {
        agent {
                docker {
                    label 'rhel7'  // both label and image
                    image 'maven:3-alpine' 
                    args '-v /root/.m2:/root/.m2' 
                }
            }
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
            }
        }
    }
}
