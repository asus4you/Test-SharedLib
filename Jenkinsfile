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
            }
        }
        stage('triggerChildJob') {
            steps {
                script {
                    def buildParams = [
                        [$class: 'StringParameterValue', name: 'PARAM1', value: params.PARAM1],
                        [$class: 'StringParameterValue', name: 'PARAM2', value: params.PARAM2]
                    ]
                        // Trigger the child job without passing any parameters explicitly
                        build job: "pipeline-triggered-job", parameters: buildParams, wait: true
                }
            }
        }
    }
}
