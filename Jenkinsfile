pipeline {
    agent any   
    // tools {
    //     gradle 'gradle'
    // }
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build & Test') {
            steps {
                sh 'chmod +x ./gradlew'
                sh './gradlew build --build-cache'
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
        success {
            echo 'Pipeline succeeded! SonarQube analysis completed.'
        }
        failure {
            echo 'Pipeline failed! Check SonarQube report for details.'
        }
    }
}
