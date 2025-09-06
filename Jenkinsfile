pipeline {
    agent none
    stages {
        stage('Build') {
            agent { label 'compile-node' }
            steps {
                git branch: 'main', url: 'https://github.com/Suprabhat187/demo-maven-project.git'
                bat 'mvn clean compile'
            }
        }
        stage('Test') {
            agent { label 'test-node' }
            steps {
                git branch: 'main', url: 'https://github.com/Suprabhat187/demo-maven-project.git'
                bat 'mvn test'
            }
        }
        stage('Package') {
            agent { label 'compile-node' }
            steps {
                git branch: 'main', url: 'https://github.com/Suprabhat187/demo-maven-project.git'
                bat 'mvn package'
            }
        }
    }
}
