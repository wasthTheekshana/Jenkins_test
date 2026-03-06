pipeline {
    agent any

    tools {
        nodejs 'NodeJS 20.0.0'
    }
    
    stages {
        stage('Checkout') {
            steps {
                git credentialsId: 'github-token',
                url: 'https://github.com/wasthTheekshana/Jenkins_test.git',
                branch: 'main'
            }
        }

        stage('Install') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test'
            }
        }
    }
}
