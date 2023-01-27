pipeline{
    agent any

    stages{
        stage('Build docker image'){
            steps{
                script{
                    dockerapp = docker.build("fabiosilva07/kube-news:${env.BUILD_ID}",'-f ./dia2/kubenews/Dockerfile ./dia2/kubenews')
                }
            }
        }
        stage('Push docker image'){
            steps{
                script{
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub'){
                        dockerapp.push('latest')
                        dockerapp.push("${env.BUILD_ID}")
                    }
                }
            }
        }
    }
}