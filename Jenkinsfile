pipeline {
    agent {
        docker {
            image 'node:20'
            args '-u root'
        }
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                credentialsId: 'github-token',
                url: 'https://github.com/wasthTheekshana/Jenkins_test.git'
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
