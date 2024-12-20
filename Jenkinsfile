pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                // Cloning the GitHub repository
                git branch: 'main', 
                    url: 'git@github.com:<username>/<repository>.git', 
                    credentialsId: '<your-credential-id>'
            }
        }
        stage('Show File Content') {
            steps {
                // List files in the repository
                sh 'ls -la'
                // Display a specific file (replace 'filename.html' with your file's name)
                sh 'cat filename.html'
            }
        }
    }
}
