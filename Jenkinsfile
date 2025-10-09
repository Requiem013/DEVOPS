pipeline {
  agent any

  // ✅ Jenkins will use these tool installations (configure them in "Global Tool Configuration")
  tools {
    jdk 'jdk-21'
    maven 'maven-3.9'
  }

  stages {

    // ✅ Checkout code from GitHub
    stage('Checkout') {
      steps {
        deleteDir() // cleans workspace before pulling
        git branch: 'master', 
            url: 'https://github.com/Requiem013/DEVOPS.git'
        sh 'echo "Code checked out successfully from GitHub."'
      }
    }

    // ✅ Build Stage
    stage('Build') {
      steps {
        sh 'mvn -version'
        sh 'echo "Simulating build stage (no source code yet)"'
      }
    }

    // ✅ Test Stage
    stage('Test') {
      steps {
        echo 'Running sample tests...'
      }
    }

    // ✅ Deploy Stage
    stage('Deploy') {
      steps {
        echo 'Deployment stage (sample only)'
      }
    }
  }

  // ✅ Post actions (always executed)
  post {
    always {
      echo "Build complete"
      cleanWs() // cleans up workspace after build
    }
  }
}
