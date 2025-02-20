@Library('java_pipeline_groovy@main') _

pipeline {
    agent { label 'slave2' }
    stages {
        stage('Checkout') {
            steps {
               // sh "rm -rf clinic"
               // sh "git clone https://github.com/nikhilachar23/clinic.git"
               // sh "cd clinic"
                checkoutcode(feature1)
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
                // sh 'mvn spring-boot:run'
                sh 'mvn spring-boot:run -Dspring-boot.run.arguments="--server.port=8084"'
               
            }
        }
    }
}
