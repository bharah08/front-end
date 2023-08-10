pipeline {
  agent {
    docker {
      image 'node:4-alpine'
    }

  }
  stages {
    stage('build') {
      steps {
        sh 'npm install'
      }
    }

    stage('unit test') {
      steps {
        sh 'npm test'
      }
    }

  }
  post {
    always {
      echo 'This pipeline is completed..'
    }

  }
}