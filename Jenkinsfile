pipeline {
    agent any

    // environment {
    //     SCANNER_HOME = tool 'sonar-scanner'
    // }

    stages {

        /*
        stage('SonarQube') {
            steps {
                withSonarQubeEnv('sonar-scanner') {
                    sh '''
                    $SCANNER_HOME/bin/sonar-scanner \
                    -Dsonar.projectKey=Microservice_Deployment \
                    -Dsonar.projectName=Microservice_Deployment \
                    -Dsonar.java.binaries=.
                    '''
                }
            }
        }
        */

        stage('adservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/Microservice_Deployment/src/adservice/') {
                            sh "docker build -t rosetechworks/adservice:latest ."
                            sh "docker push rosetechworks/adservice:latest"
                            sh "docker rmi rosetechworks/adservice:latest"
                            sh "docker system prune -a -f --volumes"
                        }
                    }
                }
            }
        }

        stage('cartservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/Microservice_Deployment/src/cartservice/src/') {
                            sh "docker build -t rosetechworks/cartservice:latest ."
                            sh "docker push rosetechworks/cartservice:latest"
                            sh "docker rmi rosetechworks/cartservice:latest"
                            sh "docker system prune -a -f --volumes"
                        }
                    }
                }
            }
        }

        stage('checkoutservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/Microservice_Deployment/src/checkoutservice/') {
                            sh "docker build -t rosetechworks/checkoutservice:latest ."
                            sh "docker push rosetechworks/checkoutservice:latest"
                            sh "docker rmi rosetechworks/checkoutservice:latest"
                            sh "docker system prune -a -f --volumes"
                        }
                    }
                }
            }
        }

        stage('currencyservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/Microservice_Deployment/src/currencyservice/') {
                            sh "docker build -t rosetechworks/currencyservice:latest ."
                            sh "docker push rosetechworks/currencyservice:latest"
                            sh "docker rmi rosetechworks/currencyservice:latest"
                            sh "docker system prune -a -f --volumes"
                        }
                    }
                }
            }
        }

        stage('emailservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/Microservice_Deployment/src/emailservice/') {
                            sh "docker build -t rosetechworks/emailservice:latest ."
                            sh "docker push rosetechworks/emailservice:latest"
                            sh "docker rmi rosetechworks/emailservice:latest"
                            sh "docker system prune -a -f --volumes"
                        }
                    }
                }
            }
        }

        stage('frontend') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/Microservice_Deployment/src/frontend/') {
                            sh "docker build -t rosetechworks/frontend:latest ."
                            sh "docker push rosetechworks/frontend:latest"
                            sh "docker rmi rosetechworks/frontend:latest"
                            sh "docker system prune -a -f --volumes"
                        }
                    }
                }
            }
        }

        stage('loadgenerator') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/Microservice_Deployment/src/loadgenerator/') {
                            sh "docker build -t rosetechworks/loadgenerator:latest ."
                            sh "docker push rosetechworks/loadgenerator:latest"
                            sh "docker rmi rosetechworks/loadgenerator:latest"
                            sh "docker system prune -a -f --volumes"
                        }
                    }
                }
            }
        }

        stage('paymentservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/Microservice_Deployment/src/paymentservice/') {
                            sh "docker build -t rosetechworks/paymentservice:latest ."
                            sh "docker push rosetechworks/paymentservice:latest"
                            sh "docker rmi rosetechworks/paymentservice:latest"
                            sh "docker system prune -a -f --volumes"
                        }
                    }
                }
            }
        }

        stage('productcatalogservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/Microservice_Deployment/src/productcatalogservice/') {
                            sh "docker build -t rosetechworks/productcatalogservice:latest ."
                            sh "docker push rosetechworks/productcatalogservice:latest"
                            sh "docker rmi rosetechworks/productcatalogservice:latest"
                            sh "docker system prune -a -f --volumes"
                        }
                    }
                }
            }
        }

        stage('recommendationservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/Microservice_Deployment/src/recommendationservice/') {
                            sh "docker build -t rosetechworks/recommendationservice:latest ."
                            sh "docker push rosetechworks/recommendationservice:latest"
                            sh "docker rmi rosetechworks/recommendationservice:latest"
                            sh "docker system prune -a -f --volumes"
                        }
                    }
                }
            }
        }

        stage('shippingservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/Microservice_Deployment/src/shippingservice/') {
                            sh "docker build -t rosetechworks/shippingservice:latest ."
                            sh "docker push rosetechworks/shippingservice:latest"
                            sh "docker rmi rosetechworks/shippingservice:latest"
                            sh "docker system prune -a -f --volumes"
                        }
                    }
                }
            }
        }

        stage('EKS-Deployment') {
            steps {
                withKubeConfig(
                    clusterName: 'my-cluster',
                    credentialsId: 'k8s',
                    namespace: 'webapps',
                    serverUrl: 'https://61E42CB112793F341E97C43BFEDDD7CE.gr7.us-east-2.eks.amazonaws.com'
                ) {
                    sh 'kubectl apply -f deployment-service.yaml'
                    sh 'kubectl get pods'
                    sh 'kubectl get svc'
                }
            }
        }
    }
}
