pipeline {
 environment {
 imagename = “dhruvg/jenkins-docker”
 registryCredential = ‘dhruvg0001’
 dockerImage = ‘’
 }
 agent any
 stages {
 stage {
 steps {
 git([url: ‘https://github.com/dhruvexecutive07/node.git', branch: ‘main’])
 }
 }
 stage(‘Building image’) {
 steps{
 script {
 dockerImage = docker.build imagename
 }
 }
 }
 stage(‘Running image’) {
 steps{
 script {
 sh “docker run ${imagename}:latest”
 }
 }
 }
 stage(‘Deploy Image’) {
 steps{
 script {
 docker.withRegistry( ‘’, registryCredential ) {
 dockerImage.push(“$BUILD_NUMBER”)
 dockerImage.push(‘latest’)
 }
 }
 }
 }
 }
}
