pipeline {
    agent any

    tools {
        // Ensure these match your Jenkins Global Tool Configuration names
        maven 'Maven' 
        jdk 'Java17' 
    }

    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                // Ensure SonarQube is configured in Jenkins System settings
                withSonarQubeEnv('SonarQubeServer') { 
                    sh 'mvn sonar:sonar'
                }
            }
        }
    }
}
