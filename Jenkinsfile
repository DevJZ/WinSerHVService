pipeline {
    agent {
        docker { image 'dcdevjbz/msbuild15:latest' }
    }
    stages {
        stage('Test') {
            steps {
                echo 'node --version'
            }
        }
    }
}