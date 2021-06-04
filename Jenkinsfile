pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps{
                git 'https://github.com/sharadrajore/cicd02062021.git'
            }
        }
        stage('Build') {
            steps{
                tool name: 'MAVEN_HOME', type: 'maven'
                bat "mvn clean install"
            }
        }
        stage('Deploy') {
            steps{
                deploy adapters: [tomcat8(credentialsId: 'tomcat_cred', path: '', url: 'http://localhost:9090/')], contextPath: null, onFailure: false, war: '**/*.war'
            }
        }
	   
    }
}