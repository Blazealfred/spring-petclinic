pipeline {
    agent any

    tools {
        maven 'Maven 3.8.6'
    }

    environment {
        JAVA_HOME = tool name: 'jdk17'
        PATH = "${JAVA_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Clone') {
            steps {
                git url: 'https://github.com/Blazealfred/spring-petclinic.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
    }
}
