pipeline {
    agent any

    tools {
        jdk 'jdk17'
        maven 'maven3'
    }

    parameters {
        choice(
            name: 'BRANCH_NAME',
            choices: ['main', 'dev', 'staging', 'feature/login', 'feature/ui'],
            description: 'Select the Git Branch'
        )
    }

    stages {

        stage('Checkout Code') {
            steps {
                echo "Selected Branch: ${params.BRANCH_NAME}"

                git branch: "${params.BRANCH_NAME}",
                    url: 'https://github.com/shanthish16/Java-project.git'
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Post-Build') {
            steps {
                echo "Build completed for branch: ${params.BRANCH_NAME}"
            }
        }
    }
}
