#!/usr/bin/env groovy

pipeline {
    agent any

    options {
        buildDiscarder(logRotator(numToKeepStr: '10'))
        timestamps()
    }
    stages {

        stage('Upload to AWS') {
            steps {
                withAWS(region:'eu-west-2',credentials:'aws-static') {
                    s3Upload(file:'index.html', bucket:'akaua-static-udacity', path:'/')
                }
            }
        }
    }

    post {
       always {
           deleteDir()
       }
    }
}
