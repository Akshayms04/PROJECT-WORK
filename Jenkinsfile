pipeline {
    agent any
    stages{
        stage('git cloned'){
            steps{
                git url: 'https://github.com/Akshayms04/PROJECT-WORK';, branch: "master"
              
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
                    sh 'sudo docker run -itd --name My-first-container04 -p 8083:80 akshu20791/edurekab1:v1'
                    }
                }
            }
        }
