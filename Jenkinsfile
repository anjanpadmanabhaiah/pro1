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
                dir('OneDrive/Desktop/banking-project/Banking-java-project')
                {
                echo 'Starting compilation'
                sh 'mvn compile'
                }
            }
        }

        stage('Run Tests') {
            steps {
                dir('OneDrive/Desktop/banking-project/Banking-java-project')
                {
                sh 'mvn test'
                }
            }
        }

        stage('QA Check') {
            steps {
                dir('OneDrive/Desktop/banking-project/Banking-java-project')
                {
                sh 'mvn checkstyle:checkstyle'
                }
            }
        }

        stage('Package Application') {
            steps {
                dir('OneDrive/Desktop/banking-project/Banking-java-project')
                {
                sh 'mvn package'
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                dir('OneDrive/Desktop/banking-project/Banking-java-project')
                {
                sh 'docker build -t myimg .'
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                dir('OneDrive/Desktop/banking-project/Banking-java-project')
                {
                sh 'docker run -dt -p 8091:8091 --name c000 myimg'
                }
            }
        }
    }
}
