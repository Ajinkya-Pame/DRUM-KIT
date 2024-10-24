pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/Ajinkya-Pame/DRUM-KIT.git'
            }
        }
        
        stage('Run HTTP Server') {
            steps {
                script {
                    // Start http-server
                    sh 'http-server -p 5000 &'
                    // Wait for a few seconds to ensure the server starts
                    sleep(10)
                }
            }
        }
        
        stage('Access Web Page') {
            steps {
                script {
                    // You can add curl commands or any HTTP requests here to verify the server is up
                    sh 'curl -I http://localhost:5000'
                }
            }
        }
        
        stage('Stop Server') {
            steps {
                script {
                    // Stop the http-server if running
                    sh 'pkill http-server'
                }
            }
        }
    }
    
    post {
        always {
            echo 'Cleaning up...'
            // Any cleanup steps can be added here
        }
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}

