pipeline {
    agent any
    stages{
        stage('git cloned'){
            steps{
                git url: 'https://github.com/Akshayms04/PROJECT-WORK.git', branch: "master"
                sh "mvn clean package"  
            }
        }
        stage('Build docker image'){
            steps{
                script{
                    sh 'docker build -t akshay04ms/staragilefinanceproject:v1 .'
                    sh 'docker images'
                }
            }
        }
          stage('Docker login') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-pwd', passwordVariable: 'PASS', usernameVariable: 'USER')]) {
                    sh "echo $PASS | docker login -u $USER --password-stdin"
                    sh 'docker push akshay04ms/staragilefinanceproject:v1'
                }
            }
        }
        
     stage('Deploy') {
            steps {
                    sh 'sudo docker run -itd --name My-first-container -p 8081:80 akshay04ms/staragilefinanceproject:v1'
                    }
                }
            }
        }
