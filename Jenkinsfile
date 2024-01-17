pipeline {
    agent any
    stages {
        stage('Build Maven') {
            steps {
                sh 'pwd'
                sh 'mvn clean install package'
            }
        }
        stage ('copy artifacts') {
            steps {
                sh 'pwd'
                sh 'cp -r target/*.jar docker'
            }
        }
        stage ('unit tests') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Build Docker Image'){
            steps{
                script {
                    def customImage = docker.build("sneha789/petclinic:${env.BUILD_NUMBER}","./docker")
                    docker.withRegistry('https://registry.hub.docker.com','dockerhub'){
                    customImage.push()    

                    }
                }
            }
        }
        stage('build on kubernetes') {
            steps {
               withKubeConfig([credentialsId: 'kubeconfig']) {
                sh 'pwd'
                sh 'cp -R helm/*.'
                sh 'ls -ltrh'
                ls 'pwd'
                sh 'user/local/bin/helm upgrade --install petclinic-app petclinic --set image.repository=ashaikh65/petclinic --set image.tag=${BUILD_NUMBER}'

            }
        }
    }
}