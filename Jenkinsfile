
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/kk3435/jenkins-git-test.git'
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t jenkins-git-test .'
            }
        }

        stage('Test') {
            steps {
                sh 'docker run --rm jenkins-git-test python -m unittest || true'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker run -d -p 5000:5000 --name jenkins-test-app jenkins-git-test'
            }
        }
    }
}

