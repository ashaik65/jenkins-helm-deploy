pipeline {
    agent any 
        stages {
            stage ('build maven') {
                steps {
                    sh 'pwd'
                    sh 'maven clean install package'

                }
            
            }
        }
    }