pipeline {
    agent any

    stages {
        stage('Clone and Clean Repo') {
            steps {
                sh 'git clone https://github.com/fanantenana1/Java_Devop.git'
                sh 'mvn clean -f Java_Devop/Fanantenana/pom.xml'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test -f Java_Devop/Fanantenana/pom.xml'
            }
        }

        stage('Deploy') {
            steps {
                sh 'mvn package -f Java_Devop/Fanantenana/pom.xml'
                sh 'mvn deploy -f Java_Devop/Fanantenana/pom.xml'
                sh 'mvn sonar:sonar -f Java_Devop/Fanantenana/pom.xml'
            }
        }
    }

    post {
        success {
            echo 'Pipeline ran successfully!'
        }
        failure {
            echo 'Pipeline failed.'
        }
        always {
            echo 'Pipeline finished.'
        }
    }
}
