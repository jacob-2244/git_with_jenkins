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
                        url: 'https://github.com/muneebahmedayub/devops-hello-world-assignment.git',
                        credentialsId: 'github' // Replace with your credential ID
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
                sshagent(['web-server']) {
                    sh '''
                    # Transfer files to the Apache2 server
                    scp -o StrictHostKeyChecking=no -r * ubuntu@13.60.223.61:/var/www/html/
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
