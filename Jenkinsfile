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
                bat 'docker login -u "talaritulasi" -p "Talari@28"'
            }
        }
        stage('push Docker Image to Docker Hub') {
            steps {
                echo 'push Docker Image to Docker Hub'
                bat 'docker tag kubdemoapp:v1 talaritulasi/sample:kubeimage1'
                bat 'docker push talaritulasi/sample:kubeimage1'

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
