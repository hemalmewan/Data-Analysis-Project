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

    stage('Build Containers') {
      steps {
        bat 'docker-compose build'
      }
    }

    stage('Run Conteiners'){
      steps{
          bat 'docker-compose up -d'
      }
    }

    stage('Test') {
      steps {
         bat '''
          echo Waiting for backend to be ready...
          powershell -Command "Start-Sleep -Seconds 15"
          curl -f http://localhost:8000/
          curl -f http://localhost:8501 || exit 1
      '''
      }
    }
  }
}

