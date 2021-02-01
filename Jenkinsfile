#!/usr/bin/env groovy

pipeline {
    agent any

    options {
        ansiColor('xterm')
    }
    tools{
        Nodejs "NodeJS15"
    }

    stages {
        stage('Setup'){
            steps{
                git url:'http://10.250.8.1:8929/root/hello-nodejs-testing.git',branch:'master' 
            }            
        }
        stage('Test'){
            steps{
                sh 'npm test'
                sh 'npm ci-test'                
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
                sh 'npm install'                
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
