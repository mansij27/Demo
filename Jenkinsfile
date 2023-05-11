pipeline{
    agent any
    stages{
        stage('Docker build'){
            steps{
                script{
                    sh 'docker build . -t mjmansi27/my-docker:$BUILD_NUMBER'
                }
            }
        }
        
        stage('Docker Login'){
            steps{
                script{
                    withCredentials([string(credentialsId: 'dockerhub-pwd', variable: 'dockerhub_pwd')]) {
                    sh 'docker login -u mjmansi27 -p $dockerhub_pwd'
                    }
                }
            }
        }
        stage('Pushing image'){
            steps{
            sh 'docker push mjmansi27/my-docker:${BUILD_NUMBER}'
            }
        }
    }
    post{
        always{
            sh 'docker logout'
        }
    }
}



