pipeline {
    agent {
        label 'AGENT-1'
    }
    environment {
        COURSE = 'Jenkins'
    }
    options {
        timeout(time: 30, unit: 'MINUTES') // Pipeline will abort after 1 hour
        disableConcurrentBuilds()
    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Specify the jenkins user name')
        booleanParam(name: 'RUN_TESTS', defaultValue: true, description: 'Run unit tests?')
    }
    stages {
        stage('Build') {
            steps {
                script {
                    echo "Building.."
                    echo "Hello,${params.PERSON}"
                }
                
            }
        }
        stage('Test'){
            steps {
                script {
                    sh """
                        echo "Hello from Test stage.."
                        env
                    """
                }
                
            }
        }
        stage('Deploy') {
                input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "alice,bob"
                parameters {
                    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
                }
            }
            steps {
                echo "Hello ${PERSON}, nice to meet you"
                echo "Deploying.."
            }
        }
    }
    post {
        always {
            echo "I will always say Hello.."
            deleteDir()
        }
        success {
            echo "Hello SUCCESS.."
        }
        failure {
            echo "Hello FAILURE..."
        }
    }    
}
