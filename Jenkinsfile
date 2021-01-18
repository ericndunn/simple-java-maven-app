/* groovylint-disable DuplicateStringLiteral, GStringExpressionWithinString, TrailingWhitespace */
pipeline {
    agent { label 'dockerserver' } // if you don't have other steps, 'any' agent works
    //env.JAVA_HOME="${tool 'JDK_8''}"
    //env.PATH="${env.JAVA_HOME}/bin:${env.PATH}"
    withEnv(['jdk = tool name: JDK_8', 'env.JAVA_HOME = "${jdk}"']) {
    // some block

    stages {
        stage('Back-end') {
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
}
