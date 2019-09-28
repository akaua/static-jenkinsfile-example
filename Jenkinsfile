#!/usr/bin/env groovy

pipeline {
    agent any

    options {
        buildDiscarder(logRotator(numToKeepStr: '10'))
        timestamps()
    }
    stages {

        stage('Build') {
            steps {
                sh '''#!/bin/bash
                 echo "hello"
                '''
            }
        }

    post {
       always {
           deleteDir()
       }
    }
}
