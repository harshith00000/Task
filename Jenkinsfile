pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git branch: 'main',
                url: 'https://github.com/harshith00000/Task.git'
            }
        }

        stage('Build') {
            steps {
                dir('task') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage('Test') {
            steps {
                dir('task') {
                    sh 'mvn test'
                }
            }
        }

        stage('Deploy') {
            steps {
                dir('task') {
                    sh '''
                    mvn package
                    cp target/task.war /opt/tomcat/webapps/
                    '''
                }
            }
        }
    }

    post {
        success {
            echo 'Build, Test and Deploy Successful'
        }

        failure {
            echo 'Pipeline Failed'
        }
    }
}
