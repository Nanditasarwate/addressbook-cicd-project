pipeline {
    agent any

    stages {
        stage('clone') {
            steps {
                echo 'cloning git remote repo...'
                git 'https://github.com/Nanditasarwate/addressbook-cicd-project.git'
            }
        }
    stage('compile') {
            steps {
                echo 'compiling the code'
                sh 'mvn compile'
                echo 'compiling completed'
            }
        }
    stage('test') {
            steps {
                echo 'Testing the code'
                sh 'mvn test'
            }
        }
    stage('QA') {
            steps {
                sh 'mvn pmd:pmd'
            }
        }   
    stage('package') {
            steps {
                sh 'mvn package'
            }
        }     
    stage("deployment of the app"){
            steps{
                sh "sudo mv /var/lib/jenkins/workspace/addressbook_deployment/target/addressbook.war /home/ubuntu/apache-tomcat-9.0.91/webapps"
            }
        }
    }
}
