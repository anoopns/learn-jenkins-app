pipeline {
    agent any
    
    environment {
        BUILD_FILE_NAME = 'output.txt'
    }

    stages {
        stage('Build') {
            steps {
                cleanWs()
                sh '''
                    pwd
                    mkdir -p build
                    echo "Testing" >> build/$BUILD_FILE_NAME
                    echo "Jenkin" >> build/$BUILD_FILE_NAME
                    cat build/$BUILD_FILE_NAME
                '''
            }
        }
        stage('Test') {
            steps {
                sh '''
                    test -f build/$BUILD_FILE_NAME
                    grep "Test" build/$BUILD_FILE_NAME
                    grep "Jenkin" build/$BUILD_FILE_NAME
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
