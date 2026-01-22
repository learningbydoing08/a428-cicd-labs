pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                dir('react-app') {
                    sh '''
                    echo "=== BUILD STAGE ===" | tee log.txt
                    docker run --rm -v "$PWD":/app -w /app node:18 \
                      sh -c "npm install && npm run build" 2>&1 | tee -a log.txt
                    '''
                }
            }
        }

        stage('Test') {
            steps {
                dir('react-app') {
                    sh '''
                    echo "=== TEST STAGE ===" | tee -a log.txt
                    docker run --rm -v "$PWD":/app -w /app node:18 \
                      sh -c "npm test -- --watch=false" 2>&1 | tee -a log.txt
                    '''
                }
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'react-app/log.txt'
        }
    }
}
