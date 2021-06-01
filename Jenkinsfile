pipeline {
    agent any
    tools {
        maven 'maven3'
    }
    stages{
        stage('Build'){
            steps{
                 sh script: 'mvn clean package'
            }
        }
        stage('Upload War To Nexus'){
            steps{
                    nexusArtifactUploader artifacts: [
                        [
                            artifactId: 'mywebapp', 
                            classifier: '', 
                            file: 'target/mywebapp-1.0.0.war', 
                            type: 'war'
                        ]
                    ], 
                    credentialsId: 'nexus3', 
                    groupId: 'in.javahome', 
                    nexusUrl: '3.129.234.9:8081', 
                    nexusVersion: 'nexus3', 
                    protocol: 'http', 
                    repository: 'simpleapp-release', 
                    version: '1.0.0'
                    }
        }
    }
}
