pipeline {
    agent any

    environment {
        APP_NAME = "jenkins-demo"
        VERSION = "1.0"
    }

    stages {

        stage('Build') {
            steps {
                sh 'echo "Building $APP_NAME version $VERSION..."'
                sh 'echo "Myself trial - this is building stage"'
            }
        }

        stage('Test') {
            steps {
                sh 'echo "Running tests..."'
                sh 'echo "All tests passed!"'
                sh 'echo "Myself trial - this is testing stage"'
            }
        }

        stage('Deploy to Staging') {
            steps {
                sh 'echo "Deploying to staging server..."'
                sh 'echo "Myself trial - this is deploying to staging stage"'
            }
        }

        stage('Deploy to Production') {
            // when {
            //     branch 'main'
            // }

            when{
                expression { env.GIT_BRANCH == 'origin/main' }
            }
            steps {
                sh 'echo "Deploying to production server..."'
                sh 'echo "Myself trial - this is deploying to production stage"'
            }
        }

    }

    post {
        success {
            echo "Pipeline passed! App is live. configured the webhook on my own, lets see"
        }
        failure {
            echo "Pipeline failed! Check the logs."
        }
        always {
            echo "Pipeline finished."
        }
    }
}