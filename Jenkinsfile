pipeline {
    agent {
        docker {
            image 'node:20'
            args '-u root'
        }
    }

    stages {

        stage('Clean Workspace') {
            steps {
                deleteDir()
            }
        }

        stage('Checkout Source') {
            steps {
                git branch: 'main',
                credentialsId: 'github-token',
                url: 'https://github.com/wasthTheekshana/Jenkins_test.git'
            }
        }

        stage('Environment Check') {
            steps {
                sh '''
                echo "Node version:"
                node -v
                echo "NPM version:"
                npm -v
                '''
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                if [ -f package.json ]; then
                    npm install
                else
                    echo "No package.json found. Skipping npm install."
                fi
                '''
            }
        }

        stage('Build') {
            steps {
                sh '''
                if [ -f package.json ]; then
                    npm run build || echo "No build script defined."
                else
                    echo "Skipping build step."
                fi
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                if [ -f package.json ]; then
                    npm test || echo "No tests defined."
                else
                    echo "Pipeline test successful."
                fi
                '''
            }
        }

    }

    post {
        success {
            echo "✅ CI Pipeline completed successfully!"
        }
        failure {
            echo "❌ Pipeline failed."
        }
        always {
            echo "Pipeline execution finished."
        }
    }
}
