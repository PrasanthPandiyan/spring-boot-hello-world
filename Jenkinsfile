pipeline {
    agent any

    tools {
        // Ensure this matches the name in Manage Jenkins -> Global Tool Configuration
        maven 'maven-3'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // If your Jenkins is running on Linux/Docker, use 'sh'. 
                // If running directly on Windows, use 'bat'.
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                echo 'Performing SonarQube Scan...'
                // You will add your SonarScanner commands here later
            }
        }
    }
    
    post {
        always {
            archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
        }
    }
}
