pipeline {
    agent any

    environment {
        GIT_REPO = 'https://github.com/Balireddy111/java_webapplication.git/'
        MAVEN_HOME = tool name: 'Maven', type: 'hudson.tasks.Maven$MavenInstallation'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git url: "${GIT_REPO}", branch: 'main'
            }
        }

        stage('Build with Maven') {
            steps {
                withMaven(maven: "${MAVEN_HOME}") {
                    sh 'mvn clean package'
                }
            }
        }

        stage('Archive WAR') {
            steps {
                archiveArtifacts artifacts: 'target/*.war', allowEmptyArchive: true
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
