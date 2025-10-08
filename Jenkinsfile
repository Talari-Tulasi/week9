pipeline{
    agent any
    stages
    {
        stage('Build Docker Image') {
            steps {
                echo "Build Docker Image"
                bat "docker build -t kubdemoapp:v1 ."
            }
        }
        stages('Docker Login') {
            steps {
                bat 'docker login -u '
            }
        }
        stage('push Docker Image to Docker Hub') {
            steps {
                echo "push Docker Image to Docker Hub"
                bat "docker tag kubdemoapp:v1 "

                bat "docker push "
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                bat'kuberct1 apply -f deployement.yaml --validate=false'
                bat 'kuberctl apply -f service.yaml'
            }

        }
    }
    post{
        success {
             echo 'Pipeleine completed successfully!'
             }
             failurer {
                echo 'Pipeline failed. Please check the logs.'
            }
    }
}