pipeline {
  agent none
  stages {
    stage('build') {
      agent {
        docker {
          image 'node:4-alpine'
        }

      }
      steps {
        sh 'npm install'
      }
    }

    stage('test') {
      agent {
        docker {
          image 'node:4-alpine'
        }

      }
      steps {
        sh 'npm test'
      }
    }

    stage('Docker B&P') {
      agent any
      steps {
        script {
          docker.withRegistry('https://index.docker.io/v1/', 'dockerlogin') {
            def dockerImage = docker.build("initcron/frontend:v${env.BUILD_ID}", "./")
            dockerImage.push()
            dockerImage.push("latest")
          }
        }

      }
    }

  }
  post {
    always {
      echo 'This pipeline is completed..'
    }

  }
}