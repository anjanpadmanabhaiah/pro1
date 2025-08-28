pipeline{
    agent any
      stage('checkout the code from github') {
        steps {
            git branch: 'main', url: 'https://github.com/anjanpadmanabhaiah/pro1.git'
            echo 'Checked out code from GitHub'
        }
    }

        stage('codecompile with anjan'){
            steps{
                echo 'starting compiling'
                sh 'mvn compile'
            }
        }
        stage('codetesting with anjan'){
            steps{
                sh 'mvn test'
            }
        }
        stage('qa with anjan'){
            steps{
                sh 'mvn checkstyle:checkstyle'
            }
        }
        stage('package with anjan'){
            steps{
                sh 'mvn package'
            }
        }
        stage('run dockerfile'){
          steps{
               sh 'docker build -t myimg .'
           }
         }
        stage('port expose'){
            steps{
                sh 'docker run -dt -p 8091:8091 --name c000 myimg'
            }
        }   
    }
}
