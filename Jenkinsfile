pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                echo "parentJob"
            }
        }
        stage('triggerChildJob') {
            steps {
                build job: "triggeredJob", wait: true
            }
        }
    }
}
