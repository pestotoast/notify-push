pipeline {
    agent any

    stages {
        stage('clone') {
            steps {
                checkout scm
            }
        }
        stage('build image') {
            steps {
                script {
                    dockerImage= docker.build("pestotoast/notify_push", "--no-cache --pull .")
                }
            }
        }
        stage('push image') {
            steps {
                script {
                    dockerImage.push()
                }
            }
        }
    }
}