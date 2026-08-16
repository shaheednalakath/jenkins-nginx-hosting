pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo '========executing checkout========'
            }
        }

        stage('Build') {
            steps {
                echo '========executing build shaheed its ok now========'
            }
        }

        stage('Test') {
            steps {
                echo '========executing test========'
            }
        }

        stage('Deploy') {
            steps {
                echo '========executing deploy========'
            }
        }
    }

    post {
        always {
            echo '========always========'
        }
        success {
            echo '========pipeline executed successfully ========'
        }
        failure {
            echo '========pipeline execution failed========'
        }
    }
}


