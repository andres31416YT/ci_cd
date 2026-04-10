pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/tu-usuario/tu-repo.git'
                // o si es local: checkout scm
            }
        }
        stage('Build') {
            steps {
                sh 'docker build -t mi-app .'
            }
        }
        stage('Test') {
            steps {
                sh 'docker run --rm mi-app npm test'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker stop mi-app-container || true'
                sh 'docker rm mi-app-container || true'
                sh 'docker run -d --name mi-app-container -p 3000:3000 mi-app'
            }
        }
    }
}
