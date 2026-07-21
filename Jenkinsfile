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
                    cp target/task.war /var/lib/tomcat10/webapps/
                    '''
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully.'
        }

        failure {
            echo 'Pipeline failed.'
        }
    }
}
