pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Starting Build'
                sh 'mkdir -p data/raw/'
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
                sh 'curl --request POST --data-binary "@data/decision_tree/model.pkl" http://model:5005/replacemodel'
            }
        }
    }
}