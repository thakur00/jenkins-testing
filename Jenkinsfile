pipeline {
    agent any

    stages {
        stage('Cleanup') {
            steps {
                cleanWs() // Clean workspace at the beginning
            }
        }

        stage('Install Dependencies and Restart PM2') {
            steps {
                script {
                    sh 'cd /jenkins/jenkins-testing && ls && git pull' // Navigate to the directory, list files, and pull latest changes
                    sh 'npm install' // Install npm packages
                    sh 'pm2 restart doo || pm2 start npm --name doo -- run start' // Restart or start the PM2 process
                }
            }
        }
    }
}
