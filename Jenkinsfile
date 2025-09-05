pipeline {
    // The Agent we are using is agent-01
    agent { label 'Agent-01' }
    
    // Define the Maven tool
    tools {
        maven 'maven3.6'
    }

    stages {
         stage('Present Dir & List Files') {
            steps {
                echo "Running in directory:"
                sh 'pwd'
                echo "Listing repository contents:"
                // This command will show you the file structure
                sh 'ls -R' 
            }
        }
        
        stage('Build & Package') {
            steps {
                // Change into the subdirectory that contains pom.xml
                dir('my-maven-project') {
                    echo 'Compiling, testing, and packaging the code...'
                    sh 'mvn clean package' 
                }
            }
        }
        
        stage('SonarQube Analysis') {
            steps {
                // Also change directory here for the Sonar analysis
                dir('my-maven-project') {
                    echo 'Running SonarQube analysis...'
                    withSonarQubeEnv('sonarqube-server') {
                        sh 'mvn sonar:sonar -Dsonar.projectName=BoardGame01 -Dsonar.projectKey=BoardGame'
                    }
                }
            }
        }
    }
}
