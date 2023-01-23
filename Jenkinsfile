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
             bat "mvn install"
            }
        }
        
        stage('Deploy') {
            steps {
                withCredentials([usernamePassword(usernameVariable: 'admin', passwordVariable: 'password')]) {
                    def server = Artifactory.server 'artifactory'
                    def uploadSpec = """{
                    "files": [
                    {
                    "pattern": "http://localhost:8082/artifactory/",
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
