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
        spets {
            sh 'pwd'
            sh 'cp -r target/*.jar docker'
        }
       }
    }
}


