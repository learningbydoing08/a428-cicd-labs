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

    stage('Manual Approval') {
      steps {
        input message: 'Lanjutkan ke tahap Deploy?'
      }
    }

    stage('Deploy') {
      steps {
        dir('react-app') {
          sh 'npm install -g serve'
          sh 'serve -s build &'
          sh 'sleep 60'
        }
      }
    }
  }
}
