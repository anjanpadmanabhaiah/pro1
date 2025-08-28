pipeline {
    agent any

    stages {
        stage('Checkout the code from GitHub') {
            steps {
                git branch: 'main', url: 'https://github.com/anjanpadmanabhaiah/pro1/'
                echo 'Checked out code from GitHub'
            }
        }

        stage('Compile Code') {
            steps {
                dir('Banking-java-project')
                {
                echo 'Starting compilation'
                sh 'mvn compile'
                }
            }
        }

        stage('Run Tests') {
            steps {
                sh 'mvn test'
            }
        }

        stage('QA Check') {
            steps {
                sh 'mvn checkstyle:checkstyle'
            }
        }

        stage('Package Application') {
            steps {
                sh 'mvn package'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t myimg .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker run -dt -p 8091:8091 --name c000 myimg'
            }
        }
    }
}
