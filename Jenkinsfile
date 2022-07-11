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
                script {
                    echo 'Veracode scanning ...'
                   withCredentials([ 
                    usernamePassword (credentialsId: 'veracode', usernameVariable: 'VERACODE_API_ID', passwordVariable: 'VERACODE_API_KEY') ]) {
                       //veracode applicationName: 'Verademo - Web - Jenkins', canFailJob: true, criticality: 'High', fileNamePattern: '', replacementPattern: '', sandboxName: '', scanExcludesPattern: '', scanIncludesPattern: '', scanName: '$timestamp', teams: '', timeout: 60, uploadIncludesPattern: 'target/verademo.war', vid: '${api_id}', vkey: '${api_key}', waitForScan: true
                        veracode applicationName: "Verademo - Web - Jenkins", criticality: 'High', debug: true, timeout: 20, fileNamePattern: '', pHost: '', pPassword: '', pUser: '', replacementPattern: '', sandboxName: '', scanExcludesPattern: '', scanIncludesPattern: '', scanName: "${BUILD_TAG}", uploadExcludesPattern: '', uploadIncludesPattern: 'target/verademo.war', vid: "${VERACODE_API_ID}", vkey: "${VERACODE_API_KEY}"
                    }
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