pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/rushi0184/Apache-Jenkins.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t apache-static-site .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                    docker rm -f apache-container || true
                    docker run -d --name apache-container -p 80:80 apache-static-site
                '''
            }
        }
    }
}
