/* groovylint-disable DuplicateMapLiteral, DuplicateStringLiteral, 
GStringExpressionWithinString, LineLength, NglParseError, TrailingWhitespace */
pipeline {
    agent { label 'dockerserver' } // if you don't have other steps, 'any' agent works

    stages {
        stage('Back-end') {
            agent {
                docker {
                  label 'dockerserver'  // both label and image
                  image 'zenika/alpine-maven:3-jdk8-onbuild'
                }
            }
            steps {
                withEnv(["JAVA_HOME=${ tool 'JDK_8' }"]) {
                sh 'mvn --version'
            }
        }
        stage('Front-end') {
            agent {
              docker {
                label 'dockerserver'  // both label and image
                image 'node:7-alpine' 
              }
            }
            steps {
                sh 'node --version'
            }
        }
    }
}

