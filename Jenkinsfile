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
                        dir('src/adservice') {
                            sh "docker build -t naomitechworks/adservice:latest ."
                            sh "docker push naomitechworks/adservice:latest"
                            sh "docker rmi naomitechworks/adservice:latest"
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
                        dir('/var/lib/jenkins/workspace/Microservice_App/src/cartservice/src/') {
                            sh "docker build -t naomitechworks/cartservice:latest ."
                            sh "docker push naomitechworks/cartservice:latest"
                            sh "docker rmi naomitechworks/cartservice:latest"
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
                        dir('/var/lib/jenkins/workspace/Microservice_App/src/checkoutservice/') {
                            sh "docker build -t naomitechworks/checkoutservice:latest ."
                            sh "docker push naomitechworks/checkoutservice:latest"
                            sh "docker rmi naomitechworks/checkoutservice:latest"
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
                        dir('/var/lib/jenkins/workspace/Microservice_App/src/currencyservice/') {
                            sh "docker build -t naomitechworks/currencyservice:latest ."
                            sh "docker push naomitechworks/currencyservice:latest"
                            sh "docker rmi naomitechworks/currencyservice:latest"
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
                        dir('/var/lib/jenkins/workspace/Microservice_App/src/emailservice/') {
                            sh "docker build -t naomitechworks/emailservice:latest ."
                            sh "docker push naomitechworks/emailservice:latest"
                            sh "docker rmi naomitechworks/emailservice:latest"
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
                        dir('/var/lib/jenkins/workspace/Microservice_App/src/frontend/') {
                            sh "docker build -t naomitechworks/frontend:latest ."
                            sh "docker push naomitechworks/frontend:latest"
                            sh "docker rmi naomitechworks/frontend:latest"
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
                        dir('/var/lib/jenkins/workspace/Microservice_App/src/loadgenerator/') {
                            sh "docker build -t naomitechworks/loadgenerator:latest ."
                            sh "docker push naomitechworks/loadgenerator:latest"
                            sh "docker rmi naomitechworks/loadgenerator:latest"
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
                        dir('/var/lib/jenkins/workspace/Microservice_App/src/paymentservice/') {
                            sh "docker build -t naomitechworks/paymentservice:latest ."
                            sh "docker push naomitechworks/paymentservice:latest"
                            sh "docker rmi naomitechworks/paymentservice:latest"
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
                        dir('/var/lib/jenkins/workspace/Microservice_App/src/productcatalogservice/') {
                            sh "docker build -t naomitechworks/productcatalogservice:latest ."
                            sh "docker push naomitechworks/productcatalogservice:latest"
                            sh "docker rmi naomitechworks/productcatalogservice:latest"
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
                        dir('/var/lib/jenkins/workspace/Microservice_App/src/recommendationservice/') {
                            sh "docker build -t naomitechworks/recommendationservice:latest ."
                            sh "docker push naomitechworks/recommendationservice:latest"
                            sh "docker rmi naomitechworks/recommendationservice:latest"
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
                        dir('/var/lib/jenkins/workspace/Microservice_App/src/shippingservice/') {
                            sh "docker build -t naomitechworks/shippingservice:latest ."
                            sh "docker push naomitechworks/shippingservice:latest"
                            sh "docker rmi naomitechworks/shippingservice:latest"
                            sh "docker system prune -a -f --volumes"
                        }
                    }
                }
            }
        }

        stage('EKS-Deployment') {
            steps {
                withKubeConfig(
                    clusterName: 'my-cluster1',
                    credentialsId: 'k8s',
                    namespace: 'webapps',
                    serverUrl: 'https://66C995335E03B26E44A90917D3DFEAC1.gr7.us-east-2.eks.amazonaws.com'
                ) {
                    sh 'kubectl apply -f deployment-service.yaml'
                    sh 'kubectl get pods'
                    sh 'kubectl get svc'
                }
            }
        }
    }
}
