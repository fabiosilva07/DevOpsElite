pipeline{
    agent any

    stages{
        stage('Build docker image'){
            steps{
                script{
                    dockerapp = docker.build("fabiosilva07/kube-news:${env.build_ID}",'-f ./dia2/kubenews/Dockerfile ./dia2/kubenews')
                }
            }
        }
    }
}