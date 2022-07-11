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
        stage('test') {
            steps {
                script {
                    echo "Testing the application..."
                }
            }
        }
    }
}