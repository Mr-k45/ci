pipeline {
 agent any
 tools {
 maven 'Maven'
 }
 stages {
 stage('Build') {
 steps {
 script {
 bat "mvn clean package"
 }
 }
 post {
 success {
 echo "Archiving the Artifacts"
 archiveArtifacts artifacts: '**/target/*.war'
 }
 }
 }
 stage('Deploy to Tomcat') {
 steps {
 script {
deploy adapters: [tomcat9(credentialsId: '8b4d5067-6763-4a52-aa87-5ac1d52d4811', path: '', url: 'http://localhost:8080')], contextPath: '/ci-cd-jk', war: '**/*.war'
 }
 }
 }
}
