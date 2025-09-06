pipeline {
    agent none

    stages {
        stage('Build') {
            agent { label 'compile-node' }
            steps {
                // Clone your repo
                git branch: 'main', url: 'https://github.com/Suprabhat187/demo-maven-project.git'

                // Optional: if you want to run inside a subdirectory, use 'dir'
                dir('demo-maven-project') {
                    // Compile without running tests
                    sh 'mvn clean compile -DskipTests'
                }
            }
        }

        stage('Test') {
            agent { label 'test-node' }
            steps {
                // Clone the repo again (or use workspace copy if you enable workspace sharing)
                git branch: 'main', url: 'https://github.com/Suprabhat187/demo-maven-project.git'

                dir('demo-maven-project') {
                    // Run unit tests
                    sh 'mvn test'
                }
            }
        }

        stage('Package') {
            agent { label 'compile-node' }
            steps {
                dir('demo-maven-project') {
                    // Package JAR
                    sh 'mvn package'
                }
            }
        }
    }
}
