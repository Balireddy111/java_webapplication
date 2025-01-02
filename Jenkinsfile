pipeline {
    agent any

    environment {
        // Define any environment variables here
        GIT_REPO = 'https://github.com/Balireddy111/java_webapplication.git/'
        MAVEN_HOME = tool name: 'Maven', type: 'hudson.tasks.Maven$MavenInstallation'
    }

    stages {
        stage('Clone Repository') {
            steps {
                // Clone the repository
                git url: "${GIT_REPO}", branch: 'main'
            }
        }

        stage('Build with Maven') {
            steps {
                // Build the project using Maven
                withMaven(maven: "${MAVEN_HOME}") {
                    sh 'mvn clean package'
                }
            }
        }
    }

    post {
        success {
            echo 'Build completed successfully!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
