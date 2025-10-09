pipeline {
  agent any

  tools {
    // Match these names exactly with what you configured in Jenkins
    jdk 'jdk-21'
    maven 'maven-3.9'
  }

  stages {

    // ✅ Checkout code from your GitHub repository
    stage('Checkout') {
      steps {
        deleteDir() // cleans workspace before checkout
        git branch: 'master',
            url: 'https://github.com/Requiem013/DEVOPS.git'  // <-- includes .git
        echo '✅ Code checked out successfully from GitHub.'
      }
    }

    // ✅ Verify environment (Java, Maven, Git)
    stage('Environment Check') {
      steps {
        bat 'echo JAVA_HOME=%JAVA_HOME%'
        bat 'java -version'
        bat 'mvn -v'
        bat 'git --version'
      }
    }

    // ✅ Build Stage
    stage('Build') {
      steps {
        bat 'mvn -B -DskipTests=true clean compile'
        echo '🏗️  Build completed successfully.'
      }
    }

    // ✅ Test Stage
    stage('Test') {
      steps {
        bat 'mvn -B test'
      }
      post {
        always {
          junit allowEmptyResults: true, testResults: '**/target/surefire-reports/*.xml'
        }
      }
    }

    // ✅ Package Stage
    stage('Package') {
      steps {
        bat 'mvn -B -DskipTests package'
        archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
        echo '📦 Packaging complete.'
      }
    }

    // ✅ Deploy (demo)
    stage('Deploy') {
      steps {
        echo '🚀 Deployment stage (demo only, no real deploy).'
      }
    }
  }

  post {
    always {
      echo '🧹 Cleaning workspace and finishing build.'
      cleanWs()
    }
  }
}
