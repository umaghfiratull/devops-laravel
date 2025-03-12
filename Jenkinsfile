pipeline {
    agent any  // Runs on any available agent

    stages {
        stage('Checkout') {
            steps {
                checkout scm  // Pulls latest code from GitHub/GitLab
            }
        }

        stage('Build') {
            agent {
                docker {
                    image 'shippingdocker/php-composer:7.4'
                    args '-u root'  // Runs as root user inside container
                }
            }
            steps {
                sh 'rm composer.lock'
                sh 'composer install'
            }
        }

        stage('Test') {
            agent {
                docker {
                    image 'ubuntu'
                    args '-u root'
                }
            }
            steps {
                sh 'echo "Ini adalah test"'
            }
        }
    }
}
