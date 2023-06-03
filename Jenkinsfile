pipeline {
  agent none
  stages {
    stage('Build') {
      agent {
        docker {
          image 'schoolofdevops/frontend'
        }

      }
      steps {
        echo 'Building..'
        sh 'npm install'
      }
    }

    stage('Test') {
      agent {
        docker {
          image 'schoolofdevops/frontend'
        }

      }
      steps {
        echo 'Testing'
        sh 'npm install'
        sh 'npm test'
      }
    }

    stage('Package') {
      agent {
        docker {
          image 'schoolofdevops/frontend'
        }

      }
      steps {
        echo 'Packaging....'
        sh 'npm install'
        sh 'npm run package'
        archiveArtifacts '**distribution/*.zip'
      }
    }

  }
  tools {
    nodejs 'nodejs-4.8.6'
  }
}