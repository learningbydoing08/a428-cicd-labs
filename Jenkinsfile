pipeline {
    agent any

    stages {
        stage('Install Dependencies') {
            steps {
                sh '''
                docker run --rm \
                  -v "$PWD/react-app:/app" \
                  -w /app \
                  node:18-alpine \
                  npm install
                '''
            }
        }

        stage('Build React App') {
            steps {
                sh '''
                docker run --rm \
                  -v "$PWD/react-app:/app" \
                  -w /app \
                  node:18-alpine \
                  npm run build
                '''
            }
        }
    }
}
