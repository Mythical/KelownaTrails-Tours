pipeline {
    agent any

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
                sh 'FIREBASE_TOKEN="$FIREBASE_TOKEN" firebase use staging'
                sh 'FIREBASE_TOKEN="$FIREBASE_TOKEN" firebase deploy --only hosting'
            }
        }

        stage('Production') {
            when {
                branch 'main'
            }
            steps {
                sh 'FIREBASE_TOKEN="$FIREBASE_TOKEN" firebase use production'
                sh 'FIREBASE_TOKEN="$FIREBASE_TOKEN" firebase deploy --only hosting'
            }
        }
    }
}

