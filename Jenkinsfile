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
        }
}  
