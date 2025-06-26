
   pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                git branch: 'test', url: 'https://github.com/aamirpatel/GeneralSpringBootProgExce.git'
                sh 'mvn clean package'
            }
        }
    }
}
