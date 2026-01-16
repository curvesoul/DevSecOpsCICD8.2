pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/curvesoul/DevSecOpsCICD8.2.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'npm test'
            }
        }

        stage('Generate Coverage Report') {
            steps {
                bat 'npm test -- --coverage'
            }
        }

        stage('NPM Audit (Security Scan)') {
            steps {
                bat 'npm audit --audit-level=high'
            }
        }

        // OPTIONAL – only if you chose SonarCloud
        stage('SonarCloud Analysis') {
            steps {
                withSonarQubeEnv('SonarCloud') {
                    bat 'sonar-scanner'
                }
            }
        }
    }
}
