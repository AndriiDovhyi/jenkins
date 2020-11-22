#!groovy
//Test jenkins pipe
properties([disableConcurrentBuilds()])

pipeline {
    agent {label 'slave'}
    options {
        buildDiscarder(logRotator(numToKeepStr: '10', artifactNumToKeepStr: '10'))
        timestamps()
    }
    stages {
        stage("Get updates") {
            steps {
                sh 'sudo apt update'
            }
        }
        stage("Setup nginx") {
            steps {
                sh 'sudo apt intall nginx -y'
            }
        }
        stage("Start nginx") {
            steps {
                sh 'sudo systemctl start nginx'
            }
        }
       stage("Chech if running nginx") {
            steps {
                sh 'sudo systemctl status nginx'
            }
        }
    }
}
