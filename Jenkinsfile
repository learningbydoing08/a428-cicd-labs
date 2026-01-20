pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                dir('react-app') {
                    sh '''
                      echo "=== BUILD STAGE ===" > build.log
                      npm install >> build.log 2>&1
                      npm run build >> build.log 2>&1
                    '''
                }
            }
        }

        stage('Test') {
            steps {
                dir('react-app') {
                    sh '''
                      echo "=== TEST STAGE ===" > test.log
                      npm test -- --watchAll=false >> test.log 2>&1
                    '''
                }
            }
        }

        stage('Generate Log') {
            steps {
                sh '''
                  cat react-app/build.log react-app/test.log > log.txt
                '''
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'log.txt'
        }
    }
}
