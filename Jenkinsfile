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
                sh 'npm install'                
            }
            //post{
                //success{
                //    archiveArtifacts 'build/libs/*.jar'
                  //  echo ".Jar Guardados en build/libs"
              //  }
            //}            
        }
        stage('Test'){
            steps{
                sh 'npm test'
                sh 'npm ci-test'                
            }
            post{
                success{
                    archiveArtifacts 'coverage/'
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
