pipeline {
    agent any

    tools {
        nodejs 'NodeJS'
        maven 'Maven' 
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/aayushi-2003/JenkinsAssignment.git', branch: 'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Run Selenium Tests') {
            steps {
                sh 'mvn test -DfailIfNoTests=false'
            }
        }
    }

    post {
        success {
            echo 'Build and tests were successful!'
        }
        failure {
            echo 'Build or tests failed!'
        }
        always {
            echo 'Cleaning up...'
        }
    }
}
