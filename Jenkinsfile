#!/usr/bin/env groovy

pipeline {
    agent any

    options {
        ansiColor('xterm')
    }
    tools{
        nodejs "NodeJS15"
    }

    stages {
        stage('Build') {
            steps {                
                sh 'yarn'                
            }          
        }
        stage('Test'){
            steps{
                sh 'yarn test'
                sh 'yarn ci-test'                
            }
            post{
                success{
                    archiveArtifacts 'coverage/'
                    cloverReportDir: 'coverage/site',
                    cloverReportFileName: 'clover.xml'
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
