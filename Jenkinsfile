pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Check out your project repository
                git branch: 'main', url: 'https://github.com/HimadriSingha/buildfile.git'
            }
        }


        stage('Deploy') {
            steps {
                // Serve the built files using serve
                dir('buildfile') {
                    sh 'serve -s build'
                }
            }
        }
    }

    post {
        always {
            // Clean up (optional)
            dir('buildfile') {
                sh 'npm prune'
            }
        }
    }
}
