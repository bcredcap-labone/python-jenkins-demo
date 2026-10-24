pipeline {
    agent any
    stages {
        stage('Checkout') { steps { checkout scm } }
        stage('Install Dependencies') {
            steps {
                sh '''
                python3 -m venv venv
                . venv/bin/activate
                pip install --upgrade pip
                pip install -r requirements.txt
                '''
            }
        }
        stage('Run Pytest') {
            steps {
                sh '''
                . venv/bin/activate
                pytest
                '''
            }
        }
        stage('Archive Report') {
            steps { archiveArtifacts artifacts: 'report.html', fingerprint: true }
        }
    }
}
