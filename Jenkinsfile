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
                step([
                    $class: 'CloverPublisher',
                    cloverReportDir: 'coverage/',
                    cloverReportFileName: 'clover.xml',
                    healthyTarget: [methodCoverage: 70, conditionalCoverage: 80, statementCoverage: 80], // optional, default is: method=70, conditional=80, statement=80
                    unhealthyTarget: [methodCoverage: 50, conditionalCoverage: 50, statementCoverage: 50], // optional, default is none
                    failingTarget: [methodCoverage: 0, conditionalCoverage: 0, statementCoverage: 0]     // optional, default is none
            ])
                sh 'yarn ci-test'     
                step([$class: "TapPublisher", testResults: "test.tap"])          
            }
       
        }
        stage('Deploy') {
            steps {
                echo "Deploy...."
            }
        }
    }
}
