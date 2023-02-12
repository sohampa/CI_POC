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

        stage('validate'){
            steps{
                echo "VALIDATE"
                bat "mvn clean validate"
            }

        }

        stage('compile'){
            steps{
                echo "COMPILE"
                bat "mvn clean compile"
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

        stage('package'){
            steps{
                echo 'Pakage'
                bat 'mvn clean package'   
            }
        }


        stage('install'){
            steps{
                echo "Install"
             bat "mvn clean install"
            }
        }
        
        stage('deploye') {
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
