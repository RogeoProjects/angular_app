pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // This step checkouts the source code from the Git repository
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Build step: Install the dependencies and build the Angular project
                sh 'npm install'
                sh 'npm run build'
            }
        }

        stage('Serve') {
            steps {
                // Step that runs Angular application server using "ng serve" command
                sh 'npm run start'
            }
        }

        // Add other steps as needed, such as automated testing, deployment, etc.
    }
}
