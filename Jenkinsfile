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
                script {
                    // Triggering the downstream job with parameters
                    build job: "/downstream-multibranch-pipeline/${params.BRANCH_NAME}", 
                          parameters: [
                              string(name: 'BRANCH_NAME', value: "${params.BRANCH_NAME}"),
                              string(name: 'PARAM1', value: "${params.PARAM1}")
                          ]
                }
            }
        }
    }
}
