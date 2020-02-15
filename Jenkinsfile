pipeline {
    agent {
        docker { 
            image 'python:3.7-slim' 
        }
    }
    stages {
        stage('Build') {
            steps {
                echo 'Starting Build'
                sh 'dvc pull model.pkl.dvc'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}