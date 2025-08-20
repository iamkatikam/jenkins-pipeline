pipeline {
    agent {
        label 'AGENT-1'
    }
    environment {
        COURSE = 'Jenkins'
    }
    options {
        timeout(time: 10, unit: 'SECONDS') // Pipeline will abort after 1 hour
    }
    stages {
        stage('Build') {
            steps {
                script {
                    echo "Building.."
                    sleep 10
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
