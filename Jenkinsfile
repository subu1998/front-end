pipeline {
  agent {
    docker {
      image 'node:4-alpine'
    }

  }
  stages {
    stage('Build') {
      steps {
        echo 'Building..'
        sh 'npm install'
      }
    }

    stage('Test') {
      steps {
        echo 'Testing'
        sh 'npm install'
        sh 'npm test'
      }
    }

    stage('Package') {
      steps {
        echo 'Packaging....'
        sh 'npm install'
        sh 'apt install zip -y'
        sh 'npm run package'
        archiveArtifacts '**distribution/*.zip'
      }
    }

  }
  tools {
    nodejs 'nodejs-4.8.6'
  }
}