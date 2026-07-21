pipeline {
    agent any

    tools {
        jdk 'jdk'
        maven 'maven'
    }

    stages {

        stage('Clone') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/harshith00000/Task.git'
            }
        }

        stage('Build') {
            steps {
                dir('Task/task') {
                    sh 'mvn clean package'
                }
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                cp Task/task/target/task.war /opt/tomcat/webapps/
                '''
            }
        }
    }

    post {
        success {
            echo "Application deployed successfully."
        }
        failure {
            echo "Deployment failed."
        }
    }
}
