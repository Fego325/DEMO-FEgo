#!/usr/bin/env groovy

pipeline {
    agent none
    stages {
       stage('test') {
            steps {
                script {
                    echo "Testing the application..."
                    echo "Executing pipeline for branch $BRANCH_NAME"
                }
            }
        }
    }
}