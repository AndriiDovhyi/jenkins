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
        stage("First") {
            steps {
                sh 'whoami'
            }
        }
        stage("Get updates") {
            steps {
                sh '/usr/bin/sudo /usr/bin/apt update'
            }
        }
        stage("Setup nginx") {
            steps {
                sh '/usr/bin/sudo /usr/bin/apt install nginx -y'
            }
        }
        stage("Start nginx") {
            steps {
                sh '/usr/bin/sudo /bin/systemctl start nginx'
            }
        }
       stage("Chech if running nginx") {
            steps {
                sh '/usr/bin/sudo /bin/systemctl status nginx'
            }
        }
    }
}
