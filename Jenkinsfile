pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                echo "Cloning repository..."
            }
        }

        stage('Build Application') {
            steps {
                echo "Building Gradle project..."
                sh 'chmod +x gradlew'
                sh './gradlew clean build'
            }
        }

        stage('Run Application') {
            steps {
                echo "Running application..."
                sh './gradlew run'
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
