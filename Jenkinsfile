pipeline {
    agent any

    stages {
        stage('Maven Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t regapp:latest .'
            }
        }

        stage('Docker Push') {
            steps {
                sh 'docker tag regapp:latest ritikkashyap/regapp:latest'
                sh 'docker push ritikkashyap/regapp:latest'
            }
        }

        stage('Kubernetes Deploy') {
            steps {
                sh 'kubectl apply -f kubernetes/deployment.yaml'
                sh 'kubectl apply -f kubernetes/loadbalancer.yaml'
            }
        }
    }
}
