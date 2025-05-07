pipeline {
    agent any

    environment {
        MVN_HOME = tool 'M3' // Nom de l'outil Maven dans Jenkins
    }

    stages {
        stage('Clean') {
            steps {
                sh '"$MVN_HOME/bin/mvn" clean -f Fanantenana/pom.xml'
            }
        }

        stage('Test') {
            steps {
                sh '"$MVN_HOME/bin/mvn" test -f Fanantenana/pom.xml'
            }
        }

        stage('Deploy') {
            steps {
                sh '"$MVN_HOME/bin/mvn" package -f Fanantenana/pom.xml'
                sh '"$MVN_HOME/bin/mvn" deploy -f Fanantenana/pom.xml'
                sh '"$MVN_HOME/bin/mvn" sonar:sonar -f Fanantenana/pom.xml'
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
