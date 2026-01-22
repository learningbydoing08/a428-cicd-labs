pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                dir('react-app') {
                    sh '''
                    echo "=== BUILD STAGE ===" | tee -a log.txt
                    npm install 2>&1 | tee -a log.txt
                    npm run build 2>&1 | tee -a log.txt
                    '''
                }
            }
        }

        stage('Test') {
            steps {
                dir('react-app') {
                    sh '''
                    echo "=== TEST STAGE ===" | tee -a log.txt
                    npm test -- --watchAll=false 2>&1 | tee -a log.txt || true
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
