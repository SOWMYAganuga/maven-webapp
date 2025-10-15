pipeline {
    agent { label 'java-slave' }
    environment {
        MAVEN_HOME = '/opt/maven'
    }
    stages {
        stage('Clone Repository') {
            steps {
                echo "Cloning Maven project from GitHub..."
                git branch: 'main', url: 'https://github.com/SOWMYAganuga/maven-webapp.git'
            }
        }
        stage('Build Project') {
            steps {
                echo "Building the Maven project..."
                sh '${MAVEN_HOME}/bin/mvn clean install'
            }
        }
    }
    post {
        success {
            echo "Build completed successfully!"
        }
        failure {
            echo "Build failed! Check console output."
        }
    }
}


