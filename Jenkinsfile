pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                docker.build('myapp')
            }
        }
        stage('Run') {
            steps {
                sh '''
                    echo 'Running..'
                    docker run -d -p 80:80 myapp
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
