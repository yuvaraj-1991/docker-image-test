pipeline {
    agent {label 'node-slave'} 

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Pulling the docker image') {
            steps {
                sh 'sudo docker pull yuv1991/maven-tomcat-test:v1'
            }
        }
        stage('Running the Docker mvn-tomcat container') {
            steps {
                sh 'sudo docker stop mvn-tomcat-deploy || true'
                sh 'sudo docker rm mvn-tomcat-deploy || true'
                sh 'sudo docker run -d --name mvn-tomcat-deploy -p 8080:8080 yuv1991/maven-tomcat-test:v1'
            }
        }
    }
}