pipeline {
    agent any

    environment {
        FIREBASE_TOKEN = credentials('FIREBASE_TOKEN')
    }

    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                echo 'Manual testing only for this assignment.'
            }
        }

        stage('Staging') {
            steps {
                sh 'firebase deploy --only hosting:staging'
            }
        }

        stage('Production') {
            when {
                branch 'main'
            }
            steps {
                sh 'firebase deploy --only hosting:production'
            }
        }
    }
}

