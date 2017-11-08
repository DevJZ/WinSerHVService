pipeline {
    agent {
        docker { image 'dcdevjbz/msbuild15:latest' }
    }
    stages {
        stage('Test') {
            steps 
            {
                docker run --rm -t dcdevjbz/msbuild15:latest
            }
        }
    }
}