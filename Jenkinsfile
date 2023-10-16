pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                sh '''
                    echo 'Cloning..'
                    ls -la
                    whoami
                    docker run hello-world
                '''
            }
        }
        stage('Build') {
            steps {
                sh '''
                    echo 'Building..'
                    docker build -t myapp .
                '''
            }
        }
        stage('Run') {
            steps {
                sh '''
                    echo 'Running..'
                    docker run -d myapp
                '''
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
