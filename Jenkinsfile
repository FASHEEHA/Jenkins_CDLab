pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Source code downloaded from GitHub'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Verify JAR') {
            steps {
                sh 'ls -l target/*.jar'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    mkdir -p /opt/temperature-deploy
                    cp target/*.jar /opt/temperature-deploy/
                '''
            }
        }
    }

    post {
        success {
            echo 'Deployment Successful!'
        }

        failure {
            echo 'Deployment Failed!'
        }
    }
}

