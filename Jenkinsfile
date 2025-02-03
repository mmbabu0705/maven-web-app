pipeline {
    agent any

    stages {
        stage('git Checkout-SCM') {
            steps {
               checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/mmbabu0705/maven-web-app.git']])
            }
        }
        stage('Compile the code') {
            steps {
               sh 'mvn compile'
            }
        }
        stage('Test the code') {
            steps {
               sh 'mvn test'
            }
        }
        stage('package the code') {
            steps {
               sh 'mvn package'
            }
        }
        stage('Deploy the code into the tomcat-server') {
            steps {
               deploy adapters: [tomcat9(credentialsId: 'tomcat_cred', path: '', url: 'http://15.206.195.251:9090/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
