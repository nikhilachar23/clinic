pipeline {
    agent { label 'slave1' }
    stages {
        stage('Checkout') {
            steps {
                sh "rm -rf clinic-1"
                sh "git clone https://github.com/poojagowda-j/clinic.git"
                sh "cd clinic"
            }
        }
        stage('Set up Environment') {
            steps {
                sh 'export JAVA_HOME=$(dirname $(dirname $(readlink -f $(which java))))'
                sh 'export MAVEN_HOME=/usr/share/maven'
            }
        }
        stage('build') {
            steps {
                sh "mvn clean install"


            }
        }
        stage('Run Application') {
            steps {
                echo 'Running Spring Boot application...'
                sh 'mvn spring-boot:run'
               
            }
        }
    }
}
