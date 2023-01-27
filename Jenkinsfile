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
        stage('Deploy Kubernetes'){
            environment{
                tag_version = "${env.BUILD_ID}"
            }
            steps{
                withKubeConfig([credentialsId: 'kubeconfig']){
                    sh 'sed -i "s/{{TAG}}/$tag_version/g" ./dia2/kubenews/k8s/deployment.yml'
                    sh 'kubectl apply -f ./dia2/kubenews/k8s/deployment.yml'
                }
            }
        }
    }
}