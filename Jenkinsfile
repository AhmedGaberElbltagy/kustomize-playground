pipeline {
    agent any   
     parameters {
        string(name: 'BRANCH', defaultValue: 'main', description: 'Branch to build')
        booleanParam(name: 'RUN_TESTS', defaultValue: true, description: 'Run tests?')
        choice(name: 'ENVIRONMENT', choices: ['dev', 'staging', 'prod'], description: 'Deployment environment')
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
                echo "Building branch ${params.BRANCH}"
                echo "Running tests: ${params.RUN_TESTS}"
                echo "Deploying to ${params.ENVIRONMENT} environment"
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
