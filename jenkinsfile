pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Check out your project repository
                git 'https://github.com/HimadriSingha/buildfile.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Install Node.js and npm
                sh 'curl -fsSL https://rpm.nodesource.com/setup_16.x | sudo bash -'
                sh 'sudo yum install -y nodejs'

                // Install Yarn (if needed)
                sh 'curl -sL https://dl.yarnpkg.com/rpm/yarn.repo | sudo tee /etc/yum.repos.d/yarn.repo'
                sh 'sudo yum install -y yarn'
            }
        }

        stage('Deploy') {
            steps {
                // Install serve globally (if not installed)
                sh 'sudo npm install -g serve'

                dir('buildfile/build') {
                    // Serve the built files using serve
                    sh 'serve -s build'
                }
            }
        }
    }

    // post {
    //     always {
    //         // Clean up (optional)
    //         dir('buildfile') {
    //             sh 'npm prune'
    //         }
    //     }
    // }
}
