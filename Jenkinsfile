    pipeline {
    agent any
    triggers {
        pollSCM '*/5 * * * *'
    }
    stages {
        stage('Build') {
            steps {
                sh '''
                apt update
                apt upgrade -y
                apt-get install python3 -y
                apt-get install python3-pip -y
                apt-get install python3-venv -y
                '''
            }
        }
        stage('Install Package') {
            steps {
                sh '''
                python3 -V
                python3 -m venv venv
                . venv/bin/activate
                pip install DateTime
                '''
            }
        }
        stage('Test code') {
            steps {
                sh '''
                python3 main.py
                '''
            }
        }
        stage('Deliver') {
            steps {
                sh '''
                echo "success"
                '''
            }
        }
    }
}