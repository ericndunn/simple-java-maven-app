/* groovylint-disable , BlockStartsWithBlankLine, DuplicateStringLiteral, FileEndsWithoutNewline, TrailingWhitespace */
// NglParseError, TrailingWhitespace
pipeline {
    agent { label 'dockerserver' }
    stages {
        stage('TEST1') {
            agent {
                docker {
                    label 'dockerserver'  // both label and image
                    image 'zenika/alpine-maven:3-jdk8-onbuild'
                }
            } 
            steps {
                sh 'printenv'
            }
        }
        stage('TEST2') {
            agent {
                docker {
                label 'dockerserver'  // both label and image
                image 'node:7-alpine' 
              }
            }
            steps {
                sh 'printenv'
            }
        }
    }
}
