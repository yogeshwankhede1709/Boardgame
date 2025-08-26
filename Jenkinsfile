pipeline {
    agent {label 'Agent-01'}
      
    tools {
        maven 'maven3.6'
        jdk 'jdk17'
    }
 
    stages {

        stage('Compile') {
            steps {
             sh 'mvn compile'
            }
        }
        stage('test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Package') {
            steps {
               sh 'mvn package'
            }
        }
        stage('Hello') {
            steps {
                echo 'Hello World Hii'
            }
        }
    }
}
