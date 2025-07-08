pipeline {
    agent any

    tools {
        maven 'Maven 3.8.5'
    }

    environment {
        DEPLOY_DIR = "/opt/tomcat/webapps" // Path to your Tomcat
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/boxfuse/boxfuse-sample-java-war-hello'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                sh 'cp target/*.war $DEPLOY_DIR/hello.war'
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
