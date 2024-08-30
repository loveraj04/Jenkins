pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Check out the code from the repository
                git url: 'https://github.com/loveraj04/Jenkins.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                // Run a build step, such as compiling code
                echo 'Building...'
                // Example for Maven: sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                // Run unit tests
                echo 'Running Tests...'
                // Example for Maven: sh 'mvn test'
            }
        }

        stage('Code Analysis') {
            steps {
                // Perform static code analysis (e.g., with SonarQube)
                echo 'Running Code Analysis...'
                // Example for SonarQube: sh 'sonar-scanner'
            }
        }

        stage('Deploy to Staging') {
            steps {
                // Deploy the build artifacts to a staging environment
                echo 'Deploying to Staging...'
                // Example SCP to a staging server: sh 'scp -i your-key.pem target/your-app.war ec2-user@staging-server:/path/to/deploy'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                // Run integration tests in staging
                echo 'Running Integration Tests on Staging...'
                // Example using Maven: sh 'mvn verify -Pstaging'
            }
        }

        stage('Deploy to Production') {
            steps {
                // Deploy the application to production
                echo 'Deploying to Production...'
                // Example SCP to production server: sh 'scp -i your-key.pem target/your-app.war ec2-user@production-server:/path/to/deploy'
            }
        }
    }

    post {
        always {
            echo 'Pipeline completed.'
        }

        success {
            echo 'Pipeline succeeded!'
            emailext(
                subject: "Jenkins Job Success: ${env.JOB_NAME}",
                body: "Good news, the Jenkins job ${env.JOB_NAME} has completed successfully.",
                to: 'your-email@example.com'
            )
        }

        failure {
            echo 'Pipeline failed!'
            emailext(
                subject: "Jenkins Job Success: ${env.JOB_NAME}",
                body: "Good news, the Jenkins job ${env.JOB_NAME} has completed successfully.",
                to: 'your-email@example.com'
            )
        }
    }
}
 