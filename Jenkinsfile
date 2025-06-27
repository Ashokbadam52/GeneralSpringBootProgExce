pipeline {
  agent any

  environment {
    SONAR_TOKEN = credentials('sonar')  // 🔐 Fetch securely
  }

  stages {
    stage('Build') {
      steps {
        git branch: 'development', url: 'https://github.com/aamirpatel/GeneralSpringBootProgExce.git'
        sh 'mvn clean package'
      }
    }

    stage('SonarQube Analysis') {
      steps {
        withSonarQubeEnv('sonar') {  // 🔍 Must match name set in Jenkins config
          sh 'mvn sonar:sonar -Dsonar.login=$SONAR_TOKEN'
        }
      }
    }

    stage('Quality Gate') {
      steps {
        timeout(time: 2, unit: 'MINUTES') {
          waitForQualityGate abortPipeline: true
        }
      }
    }
  }
}
