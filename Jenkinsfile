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
                    //archiveArtifacts 'coverage/'
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
