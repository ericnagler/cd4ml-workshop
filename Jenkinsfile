pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Starting Build'
                sh 'mkdir -p src/raw/'
                sh 'pip3 install -r requirements.txt'
                sh 'dvc repro model.pkl.dvc'
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