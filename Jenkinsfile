pipeline {
    agent any

    tools {
        nodejs 'NodeJS'
    }

    environment {
        PROJECT = 'devops-test1-dinh'
        BRANCH = 'main'
    }

    stages {
        stage('Checkout source') {
            steps {
                checkout scm
            }
        }

        stage('Install dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build project') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying website...'
                sh 'npx vercel --prod --yes --token "$VERCEL_TOKEN"'
            }
        }
    }

    post {
        success {
            echo 'BUILD SUCCESS'
        }
        failure {
            echo 'BUILD FAILED'
        }
    }
}