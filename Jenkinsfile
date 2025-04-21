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
                git url: 'https://github.com/Blazealfred/spring-petclinic', branch: 'main'
            }
        }

        stage('Build') {
            options {
                timeout(time: 10, unit: 'MINUTES') // Safeguard
            }
            steps {
                // Corrected CycloneDX property to skip the plugin
                sh 'mvn clean install -B -Dcyclonedx.skip=true'
            }
        }

        stage('Test') {
            options {
                timeout(time: 5, unit: 'MINUTES') // Safeguard
            }
            steps {
                sh 'mvn test -B'
            }
        }
    }
}
