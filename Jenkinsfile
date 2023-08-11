pipeline {
    agent any
       stages {
        stage('build maven') {
          steps {
           sh 'pwd'
           sh 'mvn clean install package'
          }
       }
    }
}


