/* groovylint-disable FileEndsWithoutNewline, TrailingWhitespace, UnusedVariable, VariableName */
pipeline {
    agent {
        docker {
            label 'dockerserver'
            image 'maven:3'
            args '-v /root/.m2:/root/.m2'
            args '-e JAVA_HOME = /usr/java/latest11'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn --version'
            }
        }
    }
}
