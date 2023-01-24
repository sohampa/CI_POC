pipeline {
    agent any
    tools {
        maven "Maven"
        jdk "Jdk"
    }

    

    stages {
        
        
//         stage('Checkout') {
//             steps {
//                 // Get some code from a GitHub repository
//                 git 'https://github.com/sohampa/CI_POC.git'
//             }
//         }
        
        stage('Initialize'){
            steps{
                echo "PATH = ${M2_HOME}/bin:${PATH}"
                echo "M2_HOME = /opt/maven"
            }
        }
        
       
        
        stage('test'){
            steps{
                echo "Test"
             bat "mvn clean test"
            }
        }
        
        
        
        stage('Sonar Analysis') {
            steps {
                // use the SonarQube Scanner to analyze the project
                withSonarQubeEnv('SONAR-SCANNER') {
                    bat 'mvn sonar:sonar'
                }
            }
        }
        
        
        stage('Compile'){
            steps{
                echo "COMPILE"
             bat "mvn clean install"
            }
        }
        
        stage('Upload_Artifact') {
            steps {
                script{
               def server = Artifactory.server 'artifactory'

                def uploadSpec = """{
                  "files": [
                    {
                      "pattern": "target/*.jar",
                      "target": "CI_POC/"
                    }
                 ]
                }"""
                server.upload(uploadSpec) 
            }
            }
        }
    
   
    }
}
