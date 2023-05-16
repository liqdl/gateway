pipeline {
    agent any
    stages {
        stage('Build') { 
            steps {
                bat 'mvn -B -DskipTests clean package' 
            }
        }
        
        stage('docker develop') {
            steps {

                // 
                bat "docker stop gateway"
                // 
                bat "docker rm gateway"
                // 
                bat "docker image rm liqdl/gateway:v1"
                // 
                bat "docker build -f .\\DockerFile.dockerfile -t liqdl/gateway:v1 ."
                // 
                bat "docker run -d -p 10010:10010 --name gateway liqdl/gateway:v1"
            }
        }
    }
}