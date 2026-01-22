pipeline {
  agent any

  tools {
    nodejs 'node18'
  }

  stages {
    stage('Build') {
      steps {
        dir('react-app') {
          sh 'npm install'
          sh 'npm run build'
        }
      }
    }

    stage('Test') {
      steps {
        dir('react-app') {
          sh 'npm test -- --watch=false'
        }
      }
    }
  }
}
