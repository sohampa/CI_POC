// comment updated
pipeline {
    agent any
    tools {
        maven "Maven"
        jdk "Jdk"
    }
    stages {
        stage('Initialize'){
            steps{
                
                echo "Initialize"
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
    post{
        always {
            jiraSendBuildInfo site: 'sohamparikjira.atlassian.net', branch: 'CP-13-Integrate-Jira-with-confluence'
            }
        }
}
