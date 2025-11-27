pipeline {
    agent any

    stages {
        stage('Pull SCM') {
            steps {
                git branch: 'gh-pages', url: 'https://github.com/ariagaluh02/hextris.git'
            }
        }
        
        stage('Build') {
            steps {
                sh'''
                docker build -t ariagaluh02/web-hextris-image:latest  .
                '''
            }
        }

        stage('Push') {
            steps {
                sh'''
                docker push ariagaluh02/web-hextris-image:latest 
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh'''
                kubectl apply -f manifest/
                '''
            }
        }   
    }
}