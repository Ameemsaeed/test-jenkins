pipeline{
    agent any

    stages{
        stage("Build"){
            steps{
                sh 'docker build -t sample-app-py'
            }
        }
        stage("Tag and push"){
            steps{
                withCredentials([usernamePassword(credentialsId: 'myCred', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh 'docker tag  sample-app-py:latest ameem/sample-app-py:latest'
                    sh "docker login -u ${USERNAME} -p ${PASSWORD}"
                    sh 'docker push ameem/sample-app-py'
                }
            }
        }
    }
}