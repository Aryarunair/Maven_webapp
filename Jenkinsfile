pipeline {
    agent any
    stages {
        stage('Checkout'){
            steps{
                checkout scm
            }
        }
            
        stage('GitHub Stage') {
            steps {
                git branch: 'main', credentialsId: 'PAT-JENKINS', url: 'https://github.com/Aryarunair/Maven_webapp.git'
            }
        }
        stage('Maven Build Stage') {
            steps {
                script {
                    def mavenHome = tool name: "maven software", type: "maven"
                    def mavenCMD = "${mavenHome}/bin/mvn"
                    sh "${mavenCMD} clean package"
                }
            }
        }
        stage('Deploy Stage') {
            steps {
                script {
                    sh 'sudo cp target/02-maven-web-app.war /home/ec2-user/apache-tomcat-9.0.89/webapps'
                }
            }
        }
    }
}
