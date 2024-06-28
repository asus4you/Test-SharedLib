pipeline {
    agent any
    
    // Define parameters for the parent job
    parameters {
        string(name: 'PARAM1', defaultValue: 'default_value1', description: 'Description for parameter 1')
        string(name: 'PARAM2', defaultValue: 'default_value2', description: 'Description for parameter 2')
    }
    
    stages {
        stage('build') {
            steps {
                echo "parentJob"
                // Use the parameters in the steps
                echo "Parameter 1: ${params.PARAM1}"
                echo "Parameter 2: ${params.PARAM2}"
                // echo "Flag: ${params.FLAG}"
            }
        }
        stage('triggerChildJob') {
            steps {
                // Trigger the child job without passing any parameters
                build job: "triggeredJob", wait: true
            }
        }
    }
}
