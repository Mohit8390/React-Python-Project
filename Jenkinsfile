pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Mohit8390/React-Python-Project.git'
            }
        }

        // -------- PYTHON --------
        stage('Test Python') {
            steps {
                dir('python-app') {
                    sh 'pip install -r requirement.txt'
                    sh 'pytest'
                }
            }
        }

        // -------- REACT --------
        stage('Build React') {
            steps {
                dir('react-app') {
                    sh 'npm install'
                    sh 'npm run build'
                }
            }
        }

    }
}