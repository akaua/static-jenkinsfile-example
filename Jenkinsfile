#!/usr/bin/env groovy

pipeline {
    agent any

    options {
        buildDiscarder(logRotator(numToKeepStr: '10'))
        timestamps()
    }
    stages {

        stage('Lint HTML') {
           steps {
               sh 'tidy -q -e *.html'
            }
        }
    

        stage('Upload to AWS') {
            steps {
                withAWS(region:'us-west-2',credentials:'aws-static') {
                    s3Upload(file:'index.html', bucket:'akaua-static-udacity', path:'')
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
