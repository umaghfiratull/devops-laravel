pipeline {
    agent any

    stages {
        stage("Checkout") {
            steps {
                cleanWs() // Ensures the workspace is empty
                checkout scm
                sh 'ls -la' // Verify files are present
            }
        }

        stage("Build") {
            steps {
                script {
                    docker.image('shippingdocker/php-composer:7.4').inside('-u root') {
                        sh 'rm -f composer.lock'
                        sh 'composer install'
                    }
                }
            }
        }

        stage("Test") {
            steps {
                script {
                    docker.image('ubuntu').inside('-u root') {
                        sh 'echo "Ini adalah test"'
                    }
                }
            }
        }
    }
}
