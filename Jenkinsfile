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
        stage('Docker Build') {
    steps {
        sh 'docker build -t my-react-app .'
    }
}
        stage('Deploy') {
    steps {
        sh '''
            docker stop my-react-container || true
            docker rm my-react-container || true
            docker run -d --name my-react-container -p 8081:80 my-react-app:latest
        '''
    }
}
    }
}
