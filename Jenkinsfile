pipeline {
    agent any
    
    environment {
        BUILD_FILE_NAME = 'output.txt'
    }

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }
        stage('Test') {
            steps {
                sh '''
                    echo 'Test stage'
                    pwd
                    file -f build/index.html
                    npm test
                '''
            }
        }

    }
}
