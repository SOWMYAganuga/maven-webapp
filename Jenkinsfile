pipeline {
    agent { label 'slave-node1' } // your Jenkins slave node label

    environment {
        MAVEN_HOME = '/opt/maven'  // make sure Maven is installed here on your slave
        PATH = "${MAVEN_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout Code') {
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

        stage('Package WAR') {
            steps {
                echo "Packaging WAR file..."
                sh 'mvn package'
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
