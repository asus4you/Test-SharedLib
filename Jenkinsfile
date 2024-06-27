pipeline {
    agent any

    parameters {
        string(name: 'BRANCH_NAME', defaultValue: 'main', description: 'Branch to build')
        string(name: 'PARAM1', defaultValue: 'value1', description: 'Parameter 1')
    }

    stages {
        stage('Build and Test') {
            steps {
                // Your build and test steps go here
                echo "Building branch: ${params.BRANCH_NAME}"
                echo "Parameter 1: ${params.PARAM1}"
            }
        }
        
        stage('Trigger Downstream Job') {
            steps {
       
