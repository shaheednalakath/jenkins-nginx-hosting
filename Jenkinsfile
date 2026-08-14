pipeline {

    agent any

    stages {

        stage('Information') {
            steps {
                sh '''
                    echo "================================"
                    echo "SYSTEM INFORMATION"
                    echo "================================"

                    echo "Current directory:"
                    pwd

                    echo "Current user:"
                    whoami

                    echo "Hostname:"
                    hostname

                    echo "Date:"
                    date
                '''
            }
        }

        stage('Build') {
            steps {
                sh '''
                    echo "================================"
                    echo "BUILD STAGE"
                    echo "================================"

                    rm -rf build
                    mkdir -p build

                    cp index.html build/
                    cp style.css build/

                    echo "Website build completed."

                    echo "Build contents:"
                    ls -la build
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                    echo "================================"
                    echo "TEST STAGE"
                    echo "================================"

                    test -f build/index.html
                    test -f build/style.css

                    echo "All required files exist."
                    echo "Test passed successfully."
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    echo "================================"
                    echo "DEPLOY STAGE"
                    echo "================================"

                    sudo mkdir -p /var/www/demo

                    sudo rm -rf /var/www/demo/*

                    sudo cp -r build/. /var/www/demo/

                    echo "Website deployed successfully."

                    echo "Deployed files:"
                    sudo ls -la /var/www/demo
                '''
            }
        }

        stage('Nginx Reload') {
            steps {
                sh '''
                    echo "================================"
                    echo "NGINX RELOAD"
                    echo "================================"

                    sudo nginx -t
                    sudo systemctl reload nginx

                    echo "Nginx reloaded successfully."
                '''
            }
        }
    }

    post {
        always {
            echo '================================'
            echo 'PIPELINE EXECUTION COMPLETED'
            echo '================================'
        }

        success {
            echo 'Website deployment SUCCESSFUL!'
        }

        failure {
            echo 'Website deployment FAILED!'
        }
    }
}