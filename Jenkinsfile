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
        string(name: 'Ramesh', defaultValue: '1.0.0', description: 'Specify the build version')
        booleanParam(name: 'RUN_TESTS', defaultValue: true, description: 'Run unit tests?')
    }
    stages {
        stage('Build') {
            steps {
                script {
                    echo "Building.."
                    echo "Hello,${params.name}"
                }
                
            }
        }
        stage('Test'){
            steps {
                script {
                    sh """
                        echo "Hello from Test.."
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
