pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/anzilcode/project2-django-docker-compose.git'
            }
        }

        stage('Deploy with Docker Compose') {
            steps {
                sh '''
                docker compose down
                docker compose build
                docker compose up -d
                docker exec django_app python manage.py migrate
                '''
            }
        }
    }

    post {
        success {
            echo 'Django + PostgreSQL deployed successfully via Jenkins!'
        }
        failure {
            echo 'Deployment failed.'
        }
    }
}
