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
            stage('Build Docker Image'){
                steps{
                    script {
                        def customImage = docker.build("xilinx19/petclinic:${env.BUILD_NUMBER}", "./docker")
                        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                        customImage.push() 

                    }
                }
            }
        }
        stage('Kubernetes'){
            steps{
                 withKubeConfig([credentialsId: 'kubeconfig']) {
                 sh 'pwd'
                 sh 'cp -R helm/* .'
                 sh 'ls -lrth'
                 sh 'pwd'
                 sh '/usr/local/bin/helm upgrade --install petclinic-app petclinic --set image.repository=xilinx19/pet --set image.tag=${BUILD_NUMBER}'
            }
        }
    }
}
}