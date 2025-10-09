pipeline {
  agent any

  tools {
    jdk 'jdk-21'
    maven 'maven-3.9'
  }

  stages {

    // ✅ FIXED CHECKOUT STAGE
    stage('Checkout') {
      steps {
        deleteDir() // clean old files in workspace
        git branch: 'master', 
            url: 'https://github.com/Requiem013/DEVOPS.git'
        sh 'echo "Code checked out successfully from GitHub."'
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
