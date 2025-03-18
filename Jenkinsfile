pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                git url: 'https://github.com/adarshpoojary07/final.git', branch: 'main'
            }
        }
        stage('Install Newman Reporter') {
            steps {
                bat 'npm install -g newman-reporter-htmlextra'
            }
        }
        stage('Run Postman Tests') {
            steps {
                bat 'newman run "2.Response validation Status code.postman_collection.json" -e "postman_environment.json" -n 2 --reporters cli,htmlextra --reporter-htmlextra-export "E:\Study_Material\POSTMAN\POSTMAN Collections\newman\final.html"'
            }
        }
        stage('Publish HTML Report') {
            steps {
                publishHTML(target: [
                    allowMissing: false,
                    alwaysLinkToLastBuild: true,
                    keepAll: true,
                    reportDir: 'E:/Study_Material/POSTMAN/POSTMAN Collections/newman',
                    reportFiles: 'Results.html',
                    reportName: 'Postman Test Report'
                ])
            }
        }
    }
}
