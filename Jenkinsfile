pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'script scripts/build.sh'
      }
    }

    stage('Test') {
      steps {
        sh 'script scripts/test.sh'
      }
    }

    stage('Build docker image') {
      steps {
        sh 'docker build  -t mybuildimage .'
      }
    }

    stage('Docker image push') {
      environment {
        registry = 'rauanamanov077/test-jenkins-pipeline'
        registryCredential = 'dockerhub_id'
      }
      steps {
        script {
          docker.withRegistry(registry, registryCredential){
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
          }
        }

      }
    }

  }
}