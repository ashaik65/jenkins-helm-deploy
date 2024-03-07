pipeline {
  agent any
    stages {
      stage('Build maven'){
        steps {
          sh 'pwd'
          sh 'mvn clean install package'
        }
      }
      stage('Copy Artifact'){
        steps{
          sh 'pwd'
          sh 'cp -r target/*.jar docker'
        }
      }
      stage('Run Test'){
        steps {
          sh 'mvn test'
        }
      }
      stage('Build Docker image'){
        steps{
          script{
            def customImage = docker.build("girijeshrichdocker02/petclinic:${env.BUILD_NUMBER}","./docker")
            docker.withRegistry('https://registry.hub.docker.com','dockerhub'){
            customImage.push()
            }
         }
        }
      }
    }
      stage('Build on Kubernetes'){
        steps {
          withKubeConfig([credentialsID:'kubeconfig']){
            sh 'pwd'
            sh 'cp -R helm/* .'
            sh 'ls -ltrh'
            sh 'pwd'
            sh '/usr/local/bin/helm upgrade --install petclinic-app petclinic --set image.repository=girijeshrichdocker02/petclinic --set image.tag=$(BUILD_NUMBER)'
          }
        }

      }
    }    
}
