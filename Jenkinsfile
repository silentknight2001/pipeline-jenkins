pipeline {
    agent any
    environment {
        DATE = new Date().format('yy.M')
        TAG = "${DATE}.${BUILD_NUMBER}"
    }
    stages {
        stage('Build docker image'){
            steps {
                script {
                    docker.build("nayan2001/web-app:${TAG}")
                }
            }
        }
        stage('Test'){
            steps{
                echo "Hi nayan"
            }
        }
        stage('Pushing Tmage to Dokerhub'){
            steps{
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'nayan'){
                        docker.image("nayan2001/web-app:${TAG}").push()
                        docker.image("nayan2001/web-app:${TAG}").push("latest")
                    }
                }
            }
        }
    }
}