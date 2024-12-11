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
        stage('Test Petclinic') {
            steps {
                script {
                    //Run Unit Test
                    sh 'mvn test'
                }
            }
            post {
                always {
                    //Archive and publish test results
                    junit '/target/surefire-reports/*.xml'
                }
            }
        }
    }
}