pipeline {
    agent { node { label 'Agent-1' } }
    options { ansiColor('xterm') }
    stages {
        stage('Install dependencies') {
           steps {
                sh 'npm install'
            }
        }
        stage('Unit testcase') {
            steps {
                echo ''
            } 
        }
                   
    }
}