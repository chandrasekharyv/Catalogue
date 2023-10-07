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
                sh 'zip -r catalogue.zip ./* --exclude=.git --exclude=.zip'
            }
        }
        stage ('Publish Artifact') {
            steps {
                nexusArtifactUploader(
                    nexusVersion: 'nexus3',
                    protocol: 'http',
                    nexusUrl: '44.201.173.7:8081/',
                    groupId: 'com.roboshop',
                    version: '1.0.0',
                    repository: 'catalogue',
                    credentialsId: 'nexus-auth',
                    artifacts: [
                        [artifactId: 'catalogue',
                        classifier: '',
                        file: 'catalogue.zip'
                        type: 'jar']
                    ]
                )
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deployment'
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