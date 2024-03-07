pipeline {
  agent any
    stages {
      stage('Build maven'){
        steps {
          sh 'pwd'
          sh 'mvn clean install package'
        }
      }
      Stage('Copy Artifact'){
        stage{
          sh 'pwd'
          sh 'cp -r target/*.jar docker'
        }
      }
    }  
}

