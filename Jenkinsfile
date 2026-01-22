pipeline {
  agent {
    docker {
      image 'node:18'
      args '-u root'
    }
  }

  stages {
    stage('Build') {
      steps {
        sh '''
          echo "=== BUILD STAGE ===" | tee log.txt
          cd react-app
          npm install 2>&1 | tee -a ../log.txt
          npm run build 2>&1 | tee -a ../log.txt
        '''
      }
    }

    stage('Test') {
      steps {
        sh '''
          echo "=== TEST STAGE ===" | tee -a log.txt
          cd react-app
          npm test -- --watch=false 2>&1 | tee -a ../log.txt
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
