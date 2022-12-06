pipeline {
    agent any
    stages{   
        stage('Clone Repository DEV') {
            agent { label 'ubuntu' }
            steps {
                git branch: 'docker', url: 'https://github.com/Fquispel/Modulo8-Docker.git'
                echo 'Cloned Django Project'
            }
        }
        stage('Build with docker-compose DEV') {
            agent { label 'ubuntu' }
            steps {
                sh 'docker-compose up -d'
                echo 'Build backend'
            }
        }
        stage('Clone Frontend Repository') {
            agent { label 'ubuntu' }
            steps {
                git branch: 'master', url: 'https://github.com/Fquispel/Lab4Modulo8.git'
                echo 'Cloned Vue Project'
            }
        }
        stage('Build frontend with docker-compose') {
            agent {label 'ubuntu'}
            steps {
                sh 'docker-compose up -d json-server'
                sh 'docker-compose up -d frontend'                
                echo 'Build frontend'
            }
        }
        stage('Clone Frontend Repository for QA') {
            agent { label 'ubuntu' }
            steps {
                git branch: 'master', url: 'https://github.com/Fquispel/Lab4Modulo8.git'
                echo 'Cloned Project for QA'
            }
        }
        stage("Run Automation test QA"){
            agent { label 'ubuntu' }
            steps {
                sh 'docker-compose up -d test'
                echo 'Build testing'
            }
        }
        stage('Clone Repository for PROD') {
            agent { label 'ubuntu' }
            steps {
                git branch: 'master', url: 'https://github.com/Fquispel/Lab4Modulo8.git'
                echo 'Cloned Vue Project'
            }
        }

        stage('Build frontend for PROD') {
            agent {label 'ubuntu'}
            steps {
                sh 'docker run -p 5000:8080 vue_project_frontend'
                echo 'Build frontend for PROD'
            }
        }
    }
}