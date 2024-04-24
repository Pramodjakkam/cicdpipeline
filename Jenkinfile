pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Checkout the source code from version control
                git 'your_repository_url_here'

                // Build Docker image
                script {
                    docker.build("your_image_name_here:${env.BUILD_ID}")
                }
            }
        }
        stage('Test') {
            steps {
                // Run your tests here if you have any
                sh 'npm test'
            }
        }
        stage('Deploy') {
            steps {
                // Push Docker image to a Docker registry
                script {
                    docker.withRegistry('https://registry.example.com', 'your_registry_credentials') {
                        docker.image("your_image_name_here:${env.BUILD_ID}").push()
                    }
                }
            }
        }
    }
}
