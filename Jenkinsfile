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

    stage('Run Tests') {
      parallel {
        stage('unit test') {
          steps {
            sh 'npm test'
          }
        }

        stage('load test') {
          steps {
            sleep 4
          }
        }

      }
    }

    stage('package') {
      steps {
        sh 'npm package'
      }
    }

  }

  post {
    always {
      echo 'This pipeline is completed..'
    }

  }
}
