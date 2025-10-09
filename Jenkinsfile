pipeline {
  agent any

  tools {
    jdk 'jdk-21'
    maven 'maven-3.9'
  }

  stages {
    stage('Checkout') {
      steps {
        checkout scm
        sh 'echo "Code checked out successfully"'
      }
    }

    stage('Build') {
      steps {
        sh 'mvn -version'
        sh 'echo "Simulating build stage (no source code yet)"'
      }
    }

    stage('Test') {
      steps {
        echo 'Running sample tests...'
      }
    }

    stage('Deploy') {
      steps {
        echo 'Deployment stage (sample only)'
      }
    }
  }

  post {
    always {
      echo "Build complete"
      cleanWs()
    }
  }
}
