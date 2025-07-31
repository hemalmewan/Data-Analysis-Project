pipeline {
  agent any

  environment {
    COMPOSE_PROJECT_NAME = "data_analysis_project"
  }

  stages {
    
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Build and Run Containers') {
      steps {
        bat 'docker-compose build'
        bat 'docker-compose up -d'
      }
    }

    stage('Test') {
      steps {
        bat '''
          timeout 15
          curl -f http://localhost:8000/docs || exit 1
          curl -f http://localhost:8501 || exit 1
        '''
      }
    }
  }
}

