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
        stage('Test'){
            steps{
                sh 'npm test'
                sh 'npm ci-test'                
            }
            post{
                succes{
                    archiveArtifacts 'coverage/'
                }
            }          
        }

        stage('Build') {
            steps {                
                sh 'npm install'                
            }
            //post{
                //success{
                //    archiveArtifacts 'build/libs/*.jar'
                  //  echo ".Jar Guardados en build/libs"
              //  }
            //}            
        }
        stage('Deploy') {
            steps {
                echo "Deploy...."
            }
        }
    }
}
