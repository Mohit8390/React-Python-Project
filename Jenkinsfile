pipeline {
    agent any

    options {
        skipDefaultCheckout(true)
    }

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
                    bat 'pip install -r requirement.txt'
                    bat 'pytest'
                }
            }
        }

        // -------- REACT --------
        stage('Install React') {
            steps {
                dir('react-app') {
                    bat 'npm install'
                }
            }
        }

        stage('Test React') {
            steps {
                dir('react-app') {
                    bat 'npm test -- --watchAll=false --passWithNoTests'
                }
            }
        }

        stage('Build React') {
            steps {
                dir('react-app') {
                    bat 'npm run build'
                }
            }
        }

        stage('Build Docker Images - Python') {
            steps {
                dir('python-app') {
                    bat 'docker build -t mohitbachhav/python-app:latest .'
                }
            }
        }

        stage('Build Docker Images - ReactJS') {
            steps {
                dir('react-app') {
                    bat 'docker build -t mohitbachhav/react-app:latest .'
                }
            }
        }

        stage('Push to DockerHub') {
            steps {
                bat 'docker build -t mohitbachhav/python-app:latest .'
                bat 'docker build -t mohitbachhav/react-app:latest .'
            }
        }
    }
}