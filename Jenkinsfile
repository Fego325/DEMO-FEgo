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
                    withCredentials([usernamePassword(credentialsId: 'veracode', passwordVariable: 'api_key', usernameVariable: 'api_id')]) {
                       veracode applicationName: 'Verademo - Web - Jenkins', canFailJob: true, criticality: 'High', fileNamePattern: '', replacementPattern: '', sandboxName: '', scanExcludesPattern: '', scanIncludesPattern: '', scanName: '$timestamp', teams: '', timeout: 60, uploadIncludesPattern: 'target/verademo.war', vid: '${api_id}', vkey: '${api_key}', waitForScan: true
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