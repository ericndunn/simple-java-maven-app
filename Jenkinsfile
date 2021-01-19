/* groovylint-disable , BlockStartsWithBlankLine, DuplicateStringLiteral, FileEndsWithoutNewline, TrailingWhitespace */
// NglParseError, TrailingWhitespace
pipeline {
    agent { label 'dockerserver' }
    stages {
        stage('Back-end') {
            agent {
                docker {
                  label 'dockerserver'  // both label and image
                  image 'zenika/alpine-maven:3-jdk8-onbuild'
                }
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
