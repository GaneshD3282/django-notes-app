@Library("Shared") _
pipeline {
    agent {label 'vinod'}

    stages {
        stage('code') {
            steps {
                script{
                    clone('https://github.com/GaneshD3282/django-notes-app.git', 'main')
                }
            }
        }
        
        stage('Build Image') {
            steps {
                script{
                    build_image("ganeshd2505","notes-app", "latest")
                }
            }
        }
        
        stage('Pushing To Git Hub') {
            steps {
                echo 'Pushing Image To Git Hub'
                script{
                    docker_push("notes-app", "latest", "ganeshd2505")
                }
            }
        }
        
        stage('Deploy') {
            steps {
               echo 'Deploying App'
               deploy()
            }
        }
    }
}
