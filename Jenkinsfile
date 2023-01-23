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
             bat "mvn test"
            }
        }
        
//         stage('Compile'){
//             steps{
//                 echo "COMPILE"
//              bat "mvn clean install"
//             }
//         }
        
//         stage('Sonar Analysis') {
//             steps {
//                 // use the SonarQube Scanner to analyze the project
//                 withSonarQubeEnv('SONAR-SCANNER') {
//                     bat 'mvn sonar:sonar'
//                 }
//             }
//         }
//         stage('Show Report') {
//             steps {
//                 // use the SonarQube plugin to display the report on the Jenkins dashboard
//                 sonarqube  server: 'SONAR-SCANNER'
//             }
//         }
    
   
    }
}
