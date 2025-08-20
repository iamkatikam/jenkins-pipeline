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
            steps {
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
