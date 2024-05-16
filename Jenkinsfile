pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Check out your project repository
                git branch: 'main', url: 'https://github.com/HimadriSingha/buildfile.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Install Node.js and npm
                sh 'curl -sL https://rpm.nodesource.com/setup_16.x | sudo bash -'
                sh 'sudo yum install -y nodejs'

                // Install Yarn (if needed)
                sh 'sudo curl -sL https://dl.yarnpkg.com/rpm/yarn.repo -o /etc/yum.repos.d/yarn.repo'
                sh 'sudo yum install -y yarn'
            }
        }


        stage('Deploy') {
            steps {
                // Install serve globally (if not installed)
                sh 'sudo npm install -g serve'

                // Serve the built files using serve
                dir('buildfile/build') {
                    sh 'serve -s .'
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
