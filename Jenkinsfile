pipeline {
    agent any
    tools {
        maven  'M2_HOME'
    }
    stages {
        stage('Build') {
            steps {
                sh script: 'mvn clean package'
            }
        }
        stage('Upload artifact to nexus'){
            steps {
                nexusArtifactUploader artifacts: [
                    [
                        artifactId: 'hello-world-maven', 
                        classifier: '', 
                        file: 'target/hello-world-app-1.0.0.jar', 
                        type: 'jar'
                    ]], 
                    credentialsId: 'nexus', 
                    groupId: 'com.aziz', 
                    nexusUrl: '192.168.99.100:8081', 
                    nexusVersion: 'nexus3', 
                    protocol: 'http', 
                    repository: 'http://192.168.99.100:8081/repository/helloworld-release/', 
                    version: '1.0.0'
            }
        }
    }
}
