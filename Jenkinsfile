pipeline {
    agent any 
        stages {
            stage ('build maven') {
                steps {
                    sh 'pwd'
                    sh 'mvn clean install package'

                }
            
            }
            stage ('copy artifacts') {
                steps{
                    sh 'pwd'
                    sh 'cp -r  target/*.jar docker'
                }
            }
            stage ("test") {
                steps {
                    sh 'mvn test'
                }
            }
            stage ("docker") {
                steps {
                    script {
                        def customImage = docker.build("xilinx19/pet:${env.BUILD_NUMBER}", "./docker" )
                        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub')
                        customImage.push()

                    }
                }
            }
        }
    }