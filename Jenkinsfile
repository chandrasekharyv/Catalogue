pipeline {
    agent { node { label 'Agent-1' } }
    options { ansiColor('xterm') }
    stages {
        stage('Install dependencies') {
           steps {
                sh 'npm install'
            }
        }
        stage('Unit test') {
            steps {
                echo 'this is unit test case'
            } 
        }
        // sonar scanner expects sonar-project.properties should be available
        // stage('Sonar Scan') {
        //     steps {
        //         sh 'ls -ltr'
        //         sh 'sonar-scanner'
        //     }
        // }
        stage('Build') {
            steps {
                sh 'ls -ltr'
                sh 'zip -r ./* --exclude=.git --exclude=.zip'
            }
        }

        
    }

    post {
        always {
            echo 'clean up workspace'
            // deleteDir()
        }
    }
    
    
}