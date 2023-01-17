pipeline {
    agent any
    tools {
        maven "Maven"
        jdk "Jdk"
    }

    

    stages {
        
        
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/sohampa/CI_POC.git'
            }
        }
        
        stage('Initialize'){
            steps{
                echo "PATH = ${M2_HOME}/bin:${PATH}"
                echo "M2_HOME = /opt/maven"
            }
        }
        
        stage('compile'){
            steps{
                echo "COMPILE"
                mvn clean install
            }
        }
    
   
    }
}
