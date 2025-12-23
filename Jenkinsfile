pipeline {
    agent any

    environment {
        // Jenkins Credentials → Secret Text → ID = vercel_token
        VERCEL_TOKEN = credentials('vercel_token')
    }

    stages {

        stage('Install') {
            steps {
                echo 'Installing dependencies'
                bat 'node -v'
                bat 'npm -v'
                bat 'npm install'
            }
        }

        stage('Build') {
            steps {
                echo 'Building React RTK project'
                bat 'npm run build'
            }
        }

        stage('Test') {
            steps {
                echo 'Skipping tests - no test script found'
                // If tests exist later:
                // bat 'npm test -- --watch=false'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying to Vercel (Production)'
                bat 'npx vercel --prod --yes --token=%VERCEL_TOKEN%'
            }
        }

    }
}
