pipeline {
    agent any
    tools {nodejs "node"}
    environment {
        imageName = "krithika11/react-app"
        registryCredential = 'krithika11'
        dockerImage = ''
    }
    stages {
        stage("Install Dependncies") {
            steps {
                sh 'npm install'
            }
        }

        stage("Tests") {
            steps {
                sh 'npm test'
            }
        }
        stage("Building Image") {
            steps {
                script {
                    dockerImage = docker.build imageName
                }
            }
        }

        stage("Deploy Image") {
            steps {
                script {
                    docker.withRegistry("https://registry.hub.docker.com", 'dockerhub-new-creds') {
                        dockerImage.push("${env.BUILD_NUMBER}")

                    }
            
                }
            }
        }   
    }
}