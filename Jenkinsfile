pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh './scripts/build.sh'
      }
    }

    stage('Test') {
      steps {
        sh './scripts/test.sh'
      }
    }

    stage('Build docker image') {
      steps {
        sh 'docker build -t mybuildimage'
      }
    }

  }
}