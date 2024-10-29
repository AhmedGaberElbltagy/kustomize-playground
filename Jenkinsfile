pipeline {
    agent any   
    tools {
        gradle 'gradle'
    }
    
    stages {
        stage('Cleanup Workspace') {
            steps {
                cleanWs()
            }
        }
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build & Test') {
            steps {
                sh 'chmod +x ./gradlew'
                sh './gradlew clean build'
            }
        }    
        
        stage('SonarQube Analysis') {
            steps {
                script {

                  sh ' ./gradlew sonar '                   
                    
                }
            }
        }
        
        stage('Quality Gate') {
            steps {
                timeout(time: 1, unit: 'HOURS') {
                    waitForQualityGate abortPipeline: true
                }
            }
        }
    }
    
    post {
        always {
            cleanWs()  
        }
        success {
            echo 'Pipeline succeeded! SonarQube analysis completed.'
        }
        failure {
            echo 'Pipeline failed! Check SonarQube report for details.'
        }
    }
}
