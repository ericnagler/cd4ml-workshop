pipeline {
    agent any
    environment { 
        MLFLOW_TRACKING_URL = 'http://mlflow:5000'
    }
    stages {
        stage('Build') {
            steps {
                echo 'Starting Build'
                sh 'mkdir -p data/raw/'
                sh 'pip3 install -r requirements.txt'
                sh 'dvc repro model.pkl.dvc'
            }
        }
        stage('Evaluate') {
            steps {
                sh 'python3 test/test.py'
            }
        }
        stage('Deploy') {
            steps {
                sh 'curl --request POST --data-binary "@data/decision_tree/model.pkl" http://model:5005/replacemodel'
            }
        }
    }
}