pipeline {
    agent any

    tools {
        maven 'test_maven'
    }

    environment {
        DEPLOY_DIR = "C:\\tomcat\\webapps" // adjust as per your Tomcat path
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/boxfuse/boxfuse-sample-java-war-hello'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                bat 'copy target\\*.war %DEPLOY_DIR%\\hello.war'
            }
        }
    }

    post {
        success {
            echo '✅ Application successfully deployed to Tomcat!'
        }
        failure {
            echo '❌ Build or deployment failed.'
        }
    }
}
