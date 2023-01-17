pipeline {
    agent any
    tools {
        maven 'maven-3.8.6' 
    }

    

    stages {
        
        
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/sohampa/CI_POC.git'
            }
        }
    
    
    stage ('Compile Stage'){
        steps{
            echo ${mvn -version}
            
        }
        
    }   
    }
}
