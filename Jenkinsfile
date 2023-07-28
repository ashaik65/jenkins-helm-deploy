pipeline {
    agent any
        stages {
            stage ('Build maven') {
                steps {
                    sh 'pwd'
                    sh 'mvn clean install package'
                }
            }
            stage ('copy artifact') {
                steps {
                    sh 'pwd'
                    sh 'cp -r target/*.jar docker'
                }
            }
            stage ( 'run test') {
                steps {
                    sh 'mvn test'
                }
            } 
            stage ( 'build docker image') {
                steps {
                    script {
                        def customImage = docker.build("monishaisha210898/petclinic:${env.BUILD_NUMBER}", "./docker")
                        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                        customImage.push()
                        }
                    }   
                }
            }
            stage ('Build on Kubernetes') {
                steps {
                    withKubeConfig([credentialsId: 'kubeconfig']) {
                        sh 'pwd'
                        sh 'cp -R helm/* .'
                        sh 'ls -ltrh'
                        sh '/usr/local/bin/helm upgrade --install petclinic-app petclinic --set image.repository=monishaisha210898/petclinic --set image.tag=${BUILD_NUMBER}'
                    }
                }
            }
        }
}
