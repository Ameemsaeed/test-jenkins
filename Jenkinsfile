pipeline{
    agent any

    stages{
        stage("Build"){
            steps{
                sh 'sudo docker build -t sample-app-py'
            }
        }
        stage("Tag and push"){
            steps{
                withCredentials([usernamePassword(credentialsId: 'myCred', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh 'sudo docker tag  sample-app-py:latest ameem/sample-app-py:latest'
                    sh "sudo docker login -u ${USERNAME} -p ${PASSWORD}"
                    sh 'sudo docker push ameem/sample-app-py'
                }
            }
        }
    }
}