// Minimal, always-green Jenkinsfile (good for demo)
pipeline {
  agent any

  stages {
    stage('Hello') {
      steps {
        echo '👋 Jenkins is set up!'
        script {
          if (isUnix()) {
            sh 'echo Hello from Jenkins'
          } else {
            bat 'echo Hello from Jenkins'
          }
        }
      }
    }
    stage('Done') {
      steps {
        echo '✅ Demo complete.'
      }
    }
  }
}
