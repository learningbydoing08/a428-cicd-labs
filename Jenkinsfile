pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh '''
                  docker run --rm \
                    -v "$PWD/react-app:/app" \
                    -w /app \
                    node:18-alpine \
                    sh -c "npm install && npm run build" \
                    | tee build.log
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                  docker run --rm \
                    -v "$PWD/react-app:/app" \
                    -w /app \
                    node:18-alpine \
                    sh -c "npm test -- --watchAll=false" \
                    | tee test.log
                '''
            }
        }

        stage('Collect Logs') {
            steps {
                sh '''
                  cat build.log test.log > log.txt
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
