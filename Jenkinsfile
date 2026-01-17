pipeline {
    agent any

    stages {

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Skipping npm test (Snyk authentication required)'
            }
        }

        stage('Generate Coverage Report') {
            steps {
                echo 'Skipping coverage report'
            }
        }

        stage('NPM Audit (Security Scan)') {
            steps {
                bat 'npm audit --audit-level=high'
            }
        }

        stage('SonarCloud Analysis') {
            steps {
                withSonarQubeEnv('SonarCloud') {
                    bat 'sonar-scanner'
                }
            }
        }
    }
}
