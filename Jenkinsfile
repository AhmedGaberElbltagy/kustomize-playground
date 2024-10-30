pipeline {
    agent any   
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
        
    
    }
}
