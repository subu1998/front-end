pipeline {
  agent any
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
        sh 'npm run package'
        archiveArtifacts '**distribution/*.zip'
      }
    }

    stage('docker build and push') {
      steps {
        script {
          docker.withRegistry('https://index.docker.io/v1/', 'dockerlogin') {
            def dockerImage = docker.build("subbu26/carts:v${env.BUILD_ID}", "./")
            dockerImage.push()

          }
        }

      }
    }

  }
  tools {
    nodejs 'nodejs-4.8.6'
  }
}