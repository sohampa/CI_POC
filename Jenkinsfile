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
        
//         stage('Compile'){
//             steps{
//                 echo "COMPILE"
//              bat "mvn -Dmaven.test.failure.ignore=true clean package"
//             }
//         }
        
        stage('Compile'){
            steps{
                echo "COMPILE"
             bat "mvn clean install"
            }
        }
        
        stage ('Upload') {
            steps {
                rtUpload (
                    // Obtain an Artifactory server instance, defined in Jenkins --> Manage Jenkins --> Configure System:
                    serverId: artifactory,
                    specPath: 'http://localhost:8082/artifactory/CI_POC/'
                )
            }
        }
    
   
    }
}
