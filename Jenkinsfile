pipeline {
    agent any
    
    parameters {
        string(name: 'PARAM1', defaultValue: 'default_value1', description: 'Description for parameter 1')
        string(name: 'PARAM2', defaultValue: 'default_value2', description: 'Description for parameter 2')
    }
    
    stages {
        stage('Build and Test') {
            steps {
                echo "Parent job: Building and testing"
                echo "Parameter 1: ${params.PARAM1}"
                echo "Parameter 2: ${params.PARAM2}"
            }
        }
        stage('Trigger Child Job') {
            steps {
                // Triggering child job with parameters
                build job: 'pipeline-triggered-job', parameters: [
                    string(name: 'PARAM1', value: "${params.PARAM1}"),
                    string(name: 'PARAM2', value: "${params.PARAM2}")
                ], wait: true
            }
        }
    }
}
