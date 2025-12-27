pipeline {
    agent any

    stages {
        stage('Git Checkout SCM') {
            steps {
                git 'https://github.com/mmbabu0705/maven-web-app.git'
            }
        }
        stage('Compile the Code') {
            steps {
                sh 'mvn compile'
            }
        }
        stage('Test the Code') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Package the Code') {
            steps {
                sh 'mvn package'
            }
        }
         stage('Deploy tomcat') {
            steps {
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'tomcat_cred', path: '', url: 'http://13.233.36.39:8080/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
