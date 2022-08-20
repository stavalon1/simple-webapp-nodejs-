pipeline {
    agent any
    stages {
        stage("Initialize") {
            steps {
                cleanWs()
            }
        }
        stage('Get SCM') {
            steps {
                git "https://github.com/Elad0109/simple-webapp-nodejs-.git"
                sh "cat Jenkinsfile"
            }
        }
        stage('Build') {
            steps {
                sh "docker build -t nodesamplespp ."
                sh "docker images"
            }
        }
        stage('Deploy') {
            steps {
                sh "docker kill nodesamplespp"
                sh "docker rm nodesamplespp"
                sh "docker run -itd --name nodesamplespp -p 3000:3000 nodesamplespp:latest &"
            }
        }
    }
}
