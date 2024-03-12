pipeline {
    agent any
    stages {
        stage('Build Maven') {
            steps {
                sh 'pwd'
                sh 'mvn clean install package'
            }
        }
        stage ('Copy Artifacts') {
            steps {
                sh 'pwd'
                sh 'cp -r target/*.jar docker'
            }
        }
        stage('Unit Tests') {
            steps {
                sh 'mvn test'
            }
        }    
        stage('Build Docker Image'){
            steps{
                script {
                    def customImage = docker.build("iran141/petclinic:${env.BUILD_NUMBER}", "./docker")
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                    customImage.push()    
                }
            }
        }
    }



