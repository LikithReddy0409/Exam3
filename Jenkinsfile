pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages {

        stage('Check-Out') {
            steps {
                git branch: 'main', url: 'https://github.com/LikithReddy0409/Exam3.git'
            }
        }

        stage('Check Chrome') {
            steps {
                sh '''
                echo "===== Chrome Information ====="
                google-chrome --version || true
                chromedriver --version || true

                echo "===== Binary Locations ====="
                which google-chrome || true
                which chromedriver || true

                echo "===== PATH ====="
                echo $PATH

                echo "===== Java ====="
                java -version
                '''
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn clean test'
            }
        }

        stage('Run-Application') {
            steps {
                sh 'mvn exec:java -Dexec.mainClass="com.example.App"'
            }
        }
    }

    post {
        success {
            echo 'Build and Deploy Successful!'
        }
        failure {
            echo 'Build Failed!'
        }
    }
}
