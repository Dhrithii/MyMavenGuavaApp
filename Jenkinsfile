pipeline {
    agent any

    tools {
        maven 'MAVEN'   // Make sure this matches Jenkins Global Tool Configuration
    }

    stages {

        stage('Build') {
            steps {
                echo 'Building the project...'
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'mvn test'
            }
        }

        stage('Check Target') {
            steps {
                echo 'Checking generated JAR file...'
                sh 'ls -l target'
            }
        }

        stage('Run Application') {
            steps {
                echo 'Running the application...'
                sh 'java -jar target/MyMavenGuavaApp-1.0-SNAPSHOT.jar'
            }
        }
    }

    post {
        success {
            echo 'Build successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
