
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM',
                    branches: [[name: '*/main']],
                    doGenerateSubmoduleConfigurations: false,
                    extensions: [],
                    userRemoteConfigs: [[
                        url: 'https://github.com/jacob-2244/first-responsive-website.git'
                    ]]
                ])
            }
        }

        stage('Build') {
            steps {
                echo 'Building project...'
                // No build step required for HTML/CSS/JS
            }
        }
        
        stage('Deploy') {
            steps {
                sshagent(['fyp']) {
                    sh '''
                    # Transfer files to the Apache2 server
                    scp -o StrictHostKeyChecking=no -r * ubuntu@13.60.209.181:/var/www/html/
                    '''
                }
            }
        }
    }

    post {
        success {
            echo 'Deployment successful!'
        }
        failure {
            echo 'Deployment failed!'
        }
    }
}
