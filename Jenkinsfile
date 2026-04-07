pipeline {
    agent any

    tools {
        maven 'maven' // must match name in Jenkins Global Tool Config
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/kushagra4647verma/maven.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Run Application') {
            steps {
                sh 'java -jar target/*.jar'
            }
        }
    }

    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
