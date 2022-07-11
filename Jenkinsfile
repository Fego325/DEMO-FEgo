#!/usr/bin/env groovy

pipeline {
    agent any

    stages {
        stage("build") {
            steps {
                script {
                    echo "building the application ..."
                    sh 'mvn package'
                }
            }
        }
        stage("veracode policy scan") {
            steps {
                echo 'Veracode scanning ...'
                withCredentials([ usernamePassword (credentialsId: 'veracode', usernameVariable: 'VERACODE_API_ID', passwordVariable: 'VERACODE_API_KEY') ]) {
                    veracode applicationName: 'Verademo - Web - Jenkins', canFailJob: true, criticality: 'High', fileNamePattern: '', replacementPattern: '', sandboxName: '', scanExcludesPattern: '', scanIncludesPattern: '', scanName: '$timestamp', teams: '', timeout: 60, uploadIncludesPattern: 'target/verademo.war',vid: "${VERACODE_API_ID}", vkey: "${VERACODE_API_KEY}", waitForScan: true
                }
            }
        }
        stage('test') {
            steps {
                script {
                    echo "Testing the application..."
                }
            }
        }
    }
}