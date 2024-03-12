pipeline{
    agent any
    stages {
        stage ('build Maven'){
            steps {
                sh 'pwd'
                sh 'mvn clean install package'
            }
        }
        stage ('copy Artifacts')
            steps {
                sh 'pwd'
                sh 'cp -r target/*.jar docker'
            }
        }
        stage (Build Docker Image){
            steps {
                script {
                    def customImage = docker.build("iran141/petclinic:${env.BUILD_NUMBER}", ./docker)
                    docker.withRegistry('https://registry.hub.docker.com', 'credentials-dockerhub') {
                    customImage.push

                }
            }

        }
    }
    stage (Build on kubernetes){
        steps {
            withKubeConfig([credentialsId: 'kubeconfig']){
                sh 'pwd'
                sh 'cp -r helm/* .'
                sh 'ls -ltrh'
                sh 'pwd'
                sh '/usr/local/bin/hemlupgrade --install petclinic-app --set image.tag=$(BUILD_NUMBER)'
                
            }
        }
    }