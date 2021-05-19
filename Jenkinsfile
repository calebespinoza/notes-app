pipeline {
    agent { label 'automation' }
    environment {
        PROJECT_NAME = "notes-app"
    }
    stages {
        stage ('Static Code Analysis') {
            steps {
                script {
                    def scannerHome = tool 'sonarqube-scanner-at'
                    withSonarQubeEnv('sonarqube-automation') {
                        sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectName=$PROJECT_NAME-Dsonar.projectKey=$PROJECT_NAME -Dsonar.sources=."
                    }
                }
            }
        }
    }
}