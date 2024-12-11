pipeline {
    agent any
    tools {
        maven 'maven'
    }

    stages {
        stage('Builds pet clinic') {
            steps {
                sh "mvn clean install"
            }
        }
    }
}
