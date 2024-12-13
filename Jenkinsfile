pipeline {
    agent any

    stages {
        stage('Clone the repository') {
            steps {
               git 'https://github.com/mmbabu0705/maven-web-app.git'
            }
        }
        stage('compile the code') {
            steps {
              sh 'mvn compile'
            }
        }
        stage('test the code') {
            steps {
              sh 'mvn test'
            }
        }
        stage('Package the war file') {
            steps {
              sh 'mvn package'
            }
        }
        stage('Deploy the war file into Tomcat-server') {
            steps {
              deploy adapters: [tomcat9(credentialsId: 'tomcat_cred', path: '', url: 'http://3.110.176.90:8080/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
