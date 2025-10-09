pipeline {
  agent any
  tools { jdk 'jdk-21'; maven 'maven-3.9' }

  parameters {
    booleanParam(name: 'RUN_MAVEN', defaultValue: false, description: 'Run Maven build/test (needs pom.xml)')
  }

  stages {
    stage('Checkout') {
      steps {
        deleteDir()
        git branch: 'master', url: 'https://github.com/Requiem013/DEVOPS.git'
        echo '✅ Code checked out successfully from GitHub.'
      }
    }

    stage('Environment Check') {
      steps {
        bat 'echo JAVA_HOME=%JAVA_HOME%'
        bat 'java -version'
        bat 'mvn -v'
        bat 'git --version'
      }
    }

    stage('Build (demo)') {
      when { expression { return !params.RUN_MAVEN } }
      steps {
        echo 'No pom.xml found — running demo-only pipeline.'
      }
    }

    stage('Build with Maven') {
      when { expression { return params.RUN_MAVEN } }
      steps {
        bat 'mvn -B -DskipTests=true clean compile'
      }
    }

    stage('Test with Maven') {
      when { expression { return params.RUN_MAVEN } }
      steps { bat 'mvn -B test' }
      post { always { junit allowEmptyResults: true, testResults: '**/target/surefire-reports/*.xml' } }
    }

    stage('Package with Maven') {
      when { expression { return params.RUN_MAVEN } }
      steps {
        bat 'mvn -B -DskipTests package'
        archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
      }
    }

    stage('Deploy (sample)') { steps { echo '🚀 Demo deploy step.' } }
  }

  post { always { echo '🧹 Cleaning workspace'; cleanWs() } }
}
