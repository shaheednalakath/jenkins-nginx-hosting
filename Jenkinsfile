pipeline {

    agent any

    stages {

        stage('Build') {
            steps {
                sh '''
                    mkdir -p build
                    cp index.html style.css build/
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                    test -f build/index.html
                    test -f build/style.css
                    echo "Test Passed"
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    sudo mkdir -p /var/www/demo
                    sudo cp -r build/* /var/www/demo/
                    sudo nginx -t
                    sudo systemctl reload nginx
                '''
            }
        }
    }

    post {
        success {
            echo 'Website Deployed Successfully!'
        }
    }
}
