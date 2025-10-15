pipeline {
    agent { label 'slave-node1' } 

    environment {
        MAVEN_HOME = '/opt/maven'       
        PATH = "${MAVEN_HOME}/bin:${env.PATH}"
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
