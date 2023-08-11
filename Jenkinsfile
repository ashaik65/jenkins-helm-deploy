pipeline {
    agent any
       stages {
        stage('build maven') {
          steps {
           sh 'pwd'
           sh 'mvn clean install package'
          }
       }
       stage('copy artifact') {
        steps {
            sh 'pwd'
            sh 'cp -r target/*.jar docker'
        }
       }
       stage('run test') {
       steps {
        sh 'mvn test'
       }
       }
    
    }
}


