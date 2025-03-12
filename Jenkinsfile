node {
    checkout scm

    // Deploy environment dev
    stage("Build") {
        docker.image('shippingdocker/php-composer:7.4').inside('-u root') {
            // Check if composer.lock exists before removing it
            sh 'if [ -f composer.lock ]; then rm composer.lock; fi'
            sh 'composer install'
        }
    }

    // Testing
    stage("Test") {
        docker.image('ubuntu').inside('-u root') {
            sh 'echo "Ini adalah test"'
        }
    }
}
