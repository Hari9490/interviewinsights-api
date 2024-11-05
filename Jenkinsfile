pipeline {
    agent { label 'node1' }


    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from your Git repository
                git branch: 'main', credentialsId: 'github-ssh-key', url: 'git@github.com:Hari9490/interviewinsights-api.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Install npm dependencies
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                // Build the React application
                sh 'npm run build'
            }
        }

        stage ('Deploy") {
               steps {
                   sh 'scp -r /home/azureuser/workspace/interviewinsights/build /var/www/deploy1/'
               }
        }
}

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
