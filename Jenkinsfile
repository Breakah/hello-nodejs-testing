#!/usr/bin/env groovy

pipeline {
    agent {
        docker { image 'node:lastest' }
    }

    options {
        ansiColor('xterm')
    }

    stages {
        stage('Setup'){
            steps{
                git url:'http://10.250.8.1:8929/root/hello-nodejs-testing.git',branch:'master' 
            }            
        }
        stage('Test'){
            steps{
                sh 'yarn test'
                sh 'yarn ci-test'                
            }
            post{
                always{
                    junit 'build/test-results/test/TEST-*.xml'  
                    jacoco(execPattern: 'build/jacoco/jacoco.exec')
                }
            }          
        }

        stage('Build') {
            steps {                
                sh 'yarn'                
            }
            post{
                success{
                    archiveArtifacts 'build/libs/*.jar'
                    echo ".Jar Guardados en build/libs"
                }
            }            
        }
        stage('Deploy') {
            steps {
                echo "Deploy...."
            }
        }
    }
}
