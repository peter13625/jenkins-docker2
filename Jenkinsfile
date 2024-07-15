pipeline {
agent any

options {
buildDiscarder(logRotator(numToKeepStr: '5'))
}

environment {
DOCKERHUB_CREDENTIALS = credentials('peter13625')
}

stages {
stage('Build') {
steps {
sh 'docker build -t peter13625/jenkins-docker-hub2 .'
}
}

stage('Login') {
steps {
sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u
$DOCKERHUB_CREDENTIALS_USR --password-stdin'
}
}

stage('Push') {
steps {
sh 'docker push peter13625/jenkins-docker-hub2'
}
}
}

post {
always {
sh 'docker logout'
}
}
}
