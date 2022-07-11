#!/usr/bin/env groovy

pipeline {
    agent any

    stage("build") {
        steps {
            script {
                echo "building the application ..."
                sh 'mvn package'
            }
        }
    }

    stages {
       stage('test') {
            steps {
                script {
                    echo "Testing the application..."
                }
            }
        }
    }
}