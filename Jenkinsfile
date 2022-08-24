pipeline {
  agent any
     tools {
      maven 'Maven 3.3.9'
      jdk 'jdk8'
    }		
    stages {      
        stage('Build maven ') {
            steps { 
              sh 'pwd'      
              sh "mvn clean package -DskipTests=true"
            }
        }
        
        stage('Copy Artifact') {
           steps { 
             sh 'pwd'
		     sh 'cp -r target/*.jar docker'
           }
        }
         
        stage('Build docker image') {
           steps {
               script {         
                 def customImage = docker.build('ashaik65/petclinic', "./docker")
                 docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                 customImage.push('latest')
                 }                     
           }
        }
	  }

      stage('Build on k8 ') {
            steps {	    
              sh 'pwd'
              sh 'cp -R helm/* .'
		      sh 'ls -ltr'
              sh 'pwd'
              sh '/usr/local/bin/helm upgrade --install petclinic-app petclinic  --set image.repository=ashaik65/petclinic --set image.tag=latest'
              			
            }           
        }
    }	    
}

