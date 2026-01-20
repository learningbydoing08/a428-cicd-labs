pipeline {
    agent any

    stages {
        stage('Install Dependencies') {
            steps {
                dir('react-app') {
                    sh 'npm install'
                }
            }
        }

        stage('Build React App') {
            steps {
                dir('react-app') {
                    sh 'npm run build'
                }
            }
        }
    }
}
