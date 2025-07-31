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
        sh 'docker-compose down || true'
        sh 'docker-compose build'
        sh 'docker-compose up -d'
      }
    }

    stage('Test') {
      steps {
        sh '''
          sleep 10
          curl -f http://localhost:8000/docs || exit 1
          curl -f http://localhost:8501 || exit 1
        '''
      }
    }

    stage('Tear Down') {
      steps {
        sh 'docker-compose down'
      }
    }
  }

  post {
    always {
      sh 'docker-compose down || true'
    }
  }
}
