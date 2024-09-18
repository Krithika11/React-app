pipeline {
    agent any
    tools {nodejs "node"}
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
    }
}