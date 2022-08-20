pipeline {
    agent any
    //agent {label "docker-slave-efc359aabf0e"}
    stages {

        stage('initws') {
            steps {
                // Clean before build
                cleanWs()
            }
        }
        stage('clone git') {
            steps {
                git branch: 'main', url: 'https://github.com/Elad0109/simple-webapp-nodejs-.git'
            }
        }
        stage('build') {
            steps { 
                sh "docker build -t nodesamplespp ."
                sh "docker images"
                
            }
        }

         stage('deploy') {
            steps { 
                sh "docker kill nodesamplespp"
                sh "docker rm nodesamplespp"
                sh "docker run -itd --name nodesamplespp -p 3000:3000 nodesamplespp:latest &"
            }
        }
    }
}
