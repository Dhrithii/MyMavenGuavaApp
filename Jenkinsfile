pipeline {
    agent any

    tools {
        maven 'MAVEN'
    }

    stages {

        stage('Build') {
            steps {
                echo 'Building project (fat JAR)...'
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
                echo 'Checking JAR...'
                sh 'ls -l target'
            }
        }

        stage('Run Application') {
            steps {
                echo 'Running shaded JAR...'
                sh 'mvn exec:JAVA -Dexec.mainClass="com.example.App"'
            }
        }
    }

    post {
        success {
            echo '✅ Build SUCCESS'
        }
        failure {
            echo '❌ Build FAILED'
        }
    }
}
