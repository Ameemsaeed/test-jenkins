pipeline{
    agent any

    stages{
        stage("Build"){
            steps{
                sh 'docker build -t sample-app-py'
            }
        }
        stage("test"){
            steps{
                sh 'test_api.sh'
            }
        }
        stage("Tag and push"){
            steps{
                withCredentials([usernamePassword(credentialsId: 'myCred', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh "docker login -u ${USERNAME} -p ${PASSWORD}"
                    sh 'docker push ameem/sample-app-py'
                }
            }
        }
    }
}