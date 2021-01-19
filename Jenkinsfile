/* groovylint-disable , BlockStartsWithBlankLine, DuplicateStringLiteral, FileEndsWithoutNewline, TrailingWhitespace */
// NglParseError, TrailingWhitespace
pipeline {
    agent { label 'dockerserver' }
    stages {
        stage('Back-end') {
            withEnv(["JAVA_HOME=${ tool 'JDK_8' }"]) {
            agent {
                docker {
                  label 'dockerserver'  // both label and image
                  image 'zenika/alpine-maven:3-jdk8-onbuild'
                }
              } 
            steps {
                sh 'mvn --version'
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
