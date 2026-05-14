pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'dev',
                url: 'https://github.com/Utkarsh-37/QuantityMeasurementAppSpringBoot.git'
            }
        }

        stage('Build Artifact') {
            steps {
                sh '''
                    cd quantity-measurement-app

                    pwd
                    ls -la

                    mvn clean package -DskipTests
                '''
            }
        }

        stage('Deploy To Backend Server') {
            steps {
                sh '''
                    cd quantity-measurement-app

                    scp target/quantity-measurement-app-0.0.1-SNAPSHOT.jar \
                    ubuntu@172.31.42.204:/app/quantity-measurement-app/target
                '''
            }
        }

        stage('Restart Application') {
            steps {
                sh '''
                    ssh ubuntu@172.31.42.204 \
                    "sudo systemctl restart quantityapp.service"
                '''
            }
        }

        stage('Verify Deployment') {
            steps {
                sh '''
                    ssh ubuntu@172.31.42.204 \
                    "sudo systemctl status quantityapp.service --no-pager"
                '''
            }
        }
    }
}
