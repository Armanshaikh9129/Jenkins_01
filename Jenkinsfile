pipeline {
    agent any

    stages {
        stage('Docker Image Build IN Dev') {
            when {
                branch 'dev'
            }
            steps {
                echo "Building Docker Image and Push into Dockerhub" 
                script {
                    def app = docker.build("armansk9129/dev:latest")
                    docker.withRegistry('https://registry.hub.docker.com', 'docker-cred') {
                        app.push()
                    }
                }
            }
        }
        
        stage('Docker Image Build IN QA') {
            when {
                branch 'qa'
            }
            steps {
                script {
                    def app = docker.build("armansk9129/qa:latest")
                    docker.withRegistry('https://registry.hub.docker.com', 'docker-cred') {
                        app.push()
                    }
                }
            }
        }
    }
    
    post {
        always {
            echo 'Deleting Project now !! '
            deleteDir()
            
            post {
                always {
                    echo 'Deleting Project now !! '
                    deleteDir()
                }
            }
       
         }

    }         
}    