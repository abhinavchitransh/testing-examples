pipeline {
    agent any
    stages {
        stage('Compile') {
            steps {
                bat 'mvn clean package -DskipTests=true'
            }
        }
        stage('Unit Tests') {
            steps {
                bat 'mvn test'
            }
        }
         stage('Integration Tests') {
            steps {
                bat 'mvn failsafe:integration-test'
            }
        }
    }
    post {
        always {
            junit 'target/surefire-reports/TEST-*.xml'
        }
        failure {
            mail to: ' ', subject: 'The Pipeline failed :(', body:'The Pipeline failed :('
        }
    }
}
