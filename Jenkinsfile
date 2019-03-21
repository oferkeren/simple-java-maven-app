pipeline {
    agent any

    stages {
        stage('checkout') {
            steps {
                deleteDir()
                checkout scm
            }
        } 
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        post {
           always {
               junit 'target/surefire-reports/*.xml'
                }
            }
    }
}
