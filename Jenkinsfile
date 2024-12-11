pipeline {
    agent any
    tools {
        maven 'maven'
    }

    stages {
        stage('Credential Scanner for detecting Secrets') {
            steps {
                script {
                    def buildUrl = env.BUILD_URL
                    sh "gitleaks detect -v --no-git --source . --report-format json --report-path secrets.json || exit 0"
                }
            }
        }
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
                    junit '**/target/surefire-reports/*.xml'
                }
            }
        }
    }
}