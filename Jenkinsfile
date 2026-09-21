pipeline {
    agent any

    tools {
        nodejs 'NodeJS-22'
    }

    stages {

        stage('Install') {
            steps {
                echo 'Installing dependencies...'
                sh 'npm install'

            }
        }

        stage('Test') {
            steps {
                sh 'CI=true npm test -- --watchAll=false'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }
    }
}
