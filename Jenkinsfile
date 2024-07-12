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
                cleanWs()
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

    }
        post {
            success {
                archiveArtifacts artifacts: 'build/**'
            }
        }
}
