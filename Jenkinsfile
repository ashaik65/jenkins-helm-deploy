pipeline {
  agent any	
    stages {      
        stage('Build maven ') {
            steps { 
              sh 'pwd'      
              sh 'mvn  clean install package'
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
                 docker.withRegistry('https://017663930438.dkr.ecr.us-east-1.amazonaws.com', 'ecr:us-east-1:my.aws.credentials') {
                 def myImage = docker.Build('jenkins-demo')    
                 myImage.push('latest')
                 }                     
           }
        }
	  }

      stage('Build on k8 ') {
            steps {
	      withKubeConfig([credentialsId: 'kubeconfig']) {
              sh 'pwd'
              sh 'cp -R helm/* .'
		      sh 'ls -ltr'
              sh 'pwd'
              sh '/usr/local/bin/helm upgrade --install petclinic-app petclinic  --set image.repository=ashaik65/petclinic --set image.tag=latest'
              			
            }           
        }
      }
    }	    
}
