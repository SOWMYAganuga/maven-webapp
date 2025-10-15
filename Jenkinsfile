pipeline {
    agent { label 'slave-node1' }
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
                sh 'mvn clean install'
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
