pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Saket-TX/SimpleJavaApp.git'
            }
        }

        stage('Build Jar') {
            steps {
                sh '/opt/homebrew/bin/mvn clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '/usr/local/bin/docker build -t myapp .'
            }
        }

        stage('Run Container') {
            steps {
                sh '/usr/local/bin/docker rm -f myapp-container || true'
                sh '/usr/local/bin/docker run -d --name myapp-container myapp'
            }
        }
    }
}
