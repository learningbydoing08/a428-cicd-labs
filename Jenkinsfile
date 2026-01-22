pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                dir('react-app') {
                    sh '''
                        echo "=== BUILD START ===" | tee ../log.txt
                        npm install 2>&1 | tee -a ../log.txt
                        npm run build 2>&1 | tee -a ../log.txt
                        echo "=== BUILD DONE ===" | tee -a ../log.txt
                    '''
                }
            }
        }

        stage('Test') {
            steps {
                dir('react-app') {
                    sh '''
                        echo "=== TEST START ===" | tee -a ../log.txt
                        npm test -- --watch=false 2>&1 | tee -a ../log.txt
                        echo "=== TEST DONE ===" | tee -a ../log.txt
                    '''
                }
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'log.txt'
        }
    }
}
