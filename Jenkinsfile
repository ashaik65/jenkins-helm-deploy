pipeline {
    agent any 
        stages {
            stage ('build maven') {
                steps {
                    sh 'pwd'
                    sh 'mvn clean install package'

                }
            
            }
            stage {
                steps{
                    sh 'pwd'
                    sh 'cp -r  target/*.jar docker'
                }
            }
            stage {
                steps {
                    sh 'mvn test'
                }
            }
        }
    }