pipeline {
    agent any
    stages {
        stage('compute') {
            steps {
                bat 'javac Factorial.java TestFactorial.java'
            }
        }
        stage('Test') {
            steps {
                bat 'java TestFactorial'
            }
        }
        stage('Run') {
            steps {
                bat 'java Factorial'
            }
        }
        stage('Package JAR') {
            steps {
                bat 'jar cfm Factorial.jar manifest.txt Factorial.class'
            }
        }
        stage('Archive JAR') {
            steps {
                archiveArtifacts artifacts: 'Factorial.jar'
            }
        }
    }
    post {
        success {
            echo 'Build, test, run, and JAR action successful — artifact ready.'
        }
        failure {
            echo 'Build failed.'
        }
    }
}
