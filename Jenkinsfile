/* groovylint-disable DuplicateStringLiteral, GStringExpressionWithinString, TrailingWhitespace */
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
                jdk = tool name: 'JDK_8'
                env.JAVA_HOME = "${jdk}"
                echo "jdk installation path is: ${jdk}"
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

