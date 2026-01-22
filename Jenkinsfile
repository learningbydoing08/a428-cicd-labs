pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                dir('react-app') {
                    sh '''
                    npm install 2>&1 | tee ../log.txt
                    '''
                }
            }
        }

        stage('Test') {
            steps {
                dir('react-app') {
                    sh '''
                    npm test -- --watch=false 2>&1 | tee -a ../log.txt
                    '''
                }
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'log.txt', fingerprint: true
        }
    }
}
