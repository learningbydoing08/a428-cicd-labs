pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh '''
                  echo "=== BUILD STAGE ===" > log.txt
                  echo "Build executed successfully" >> log.txt
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                  echo "=== TEST STAGE ===" >> log.txt
                  echo "Test executed successfully" >> log.txt
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
