pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'dotnet build'
            }
        }
        stage('Test') {
            steps {
                sh 'dotnet test'
            }
        }
        stage('Publish') {
            steps {
                sh 'dotnet publish -c Release -o ./publish'
            }
        }
        stage('Dockerize') {
            steps {
                sh 'docker build -t mydevopsapp:latest .'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker run -d -p 80:80 mydevopsapp:latest'
            }
        }
    }
}