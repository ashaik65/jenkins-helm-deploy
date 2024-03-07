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
        stage{
          sh 'pwd'
          sh 'cp -r target/*.jar docker'
        }
      }
    }  
}

