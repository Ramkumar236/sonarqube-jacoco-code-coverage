pipeline {
    agent { label 'linux' }
    stages {
        stage('Clone sources') {
            steps {
                git url: 'https://github.com/Ramkumar236/sonarqube-jacoco-code-coverage.git'
            }
        }
        stage('SonarQube analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh "./gradlew sonarqube"
                }
            }
        }
        stage("Quality gate") {
            steps {
                waitForQualityGate abortPipeline: true
            }
        }
    }
}
