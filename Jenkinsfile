pipeline {
  agent any
  tools { jdk 'jdk-21'; maven 'maven-3.9' }

  stages {
    stage('Checkout') {
      steps {
        sh 'echo "Repo already checked out by Jenkins (Declarative: Checkout SCM)."'
      }
    }
    stage('Build')  { steps { sh 'mvn -version && echo "Build stage (demo)"' } }
    stage('Test')   { steps { echo 'Running sample tests...' } }
    stage('Deploy') { steps { echo 'Deployment stage (sample only)' } }
  }

  post { always { cleanWs() } }
}
