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
        stage('upload wat to nexus'){
            steps{
                nexusArtifactUploader artifacts: [
                    [
                        artifactId: 'simple-app', 
                        classifier: '', 
                        file: 'target/simple-app-3.0.0-SNAPSHOT.war', 
                        type: 'war'
                    ]
                ], 
                credentialsId: 'nexus_project', 
                groupId: 'in.javahome', 
                nexusUrl: '52.91.103.158:8081', 
                nexusVersion: 'nexus3', 
                protocol: 'http', 
                repository: 'moopuri', 
                version: '3.0.0-SNAPSHOT.war'
            }
        }
    }
}
