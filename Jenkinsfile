pipeline {
    agent any

    stages {

        stage('Build Maven') {
            steps {
                sh 'java -version'
                sh 'mvn -version'
                sh 'mvn clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t demo-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker rm -f demo-container || true'
                sh 'docker run -d -p 9090:8080 --name demo-container demo-app'
            }
        }
    }
}
