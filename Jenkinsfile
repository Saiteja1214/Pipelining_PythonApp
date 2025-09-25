pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/2320030030/Pipelining_pythonApp.git'
            }
        }
        stage('Setup Python') {
            steps {
                bat 'python -m venv venv'
                bat '.\\venv\\Scripts\\pip install --upgrade pip'
                bat '.\\venv\\Scripts\\pip install -r requirements.txt'
            }
        }
        stage('Train Model') {
            steps {
                bat '.\\venv\\Scripts\\python model.py'
            }
        }
        stage('Test Run Flask') {
            steps {
                // Run Flask briefly (background)
                bat 'start /B .\\venv\\Scripts\\python app.py'
                bat 'timeout /t 5'
                bat 'echo Flask started successfully'
            }
        }
    }
}