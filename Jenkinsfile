pipeline {
    agent any

    environment {
        JAVA_HOME = "/usr/lib/jvm/java-17-openjdk-amd64"
        PATH = "${JAVA_HOME}/bin:${env.PATH}"
    }

    stages {

        stage('Checkout Code') {
            steps {
                echo "Cloning repository..."
                checkout scm
            }
        }

        stage('Build Application') {
            steps {
                echo "Building Gradle project..."
                sh 'java -version'
                sh 'chmod +x gradlew'
                sh './gradlew clean build --no-daemon'
            }
        }

        stage('Run Application') {
            steps {
                echo "Running application..."
                sh './gradlew run --no-daemon'
            }
        }
    }

    post {
        success {
            echo "BUILD SUCCESSFUL 🎉"
        }
        failure {
            echo "BUILD FAILED ❌"
        }
        always {
            echo "Pipeline execution completed."
        }
    }
}
