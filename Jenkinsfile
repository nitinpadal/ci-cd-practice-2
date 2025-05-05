pipeline {
    agent any

    stages {
        stage('pull code') {
            steps {
                script {
                    // Check if the directory exists and delete it if so, before cloning
                    if (fileExists('ci-cd-practice-2')) {
                        deleteDir()  // Deletes the existing 'ci-cd-practice-2' directory
                    }
                    // Clone the repository
                    bat 'git clone https://github.com/nitinpadal/ci-cd-practice-2.git'
                }
            }
        }

        stage('build a docker image') {
            steps {
                dir('ci-cd-practice-2') {
                    // Build the Docker image inside the cloned repo
                    bat 'docker build -t nitinpadal/practice4 .'
                }
            }
        }

        stage('push the image into docker hub') {
            steps {
                // Push the Docker image to Docker Hub
                bat 'docker push nitinpadal/practice4'
            }
        }
    }
}
