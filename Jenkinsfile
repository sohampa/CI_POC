pipeline {
    agent any

    

    stages {
        
        
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/sohampa/CI_POC.git'
            }
        }
    
    
    stage ('Compile Stage'){
        steps{
            withMaven(maven : 'maven_3_5_0'){
                bat 'mvn clean compile'
            }
        }
        
    }   
    }
}
