
pipeline {
    agent any

    stages {

        stage('PULL') {
            steps {
                git 'https://github.com/Gaurav1244/cdec-21.git'
            }
        }

        stage('BUILD') {
            steps {
                dir('backend') {
                    sh '''
                    mvn clean package -DskipTests
                    '''
                }
            }
        }

        stage('TEST') {
            steps {
                echo "TEST SUCCESS"
            }
        }

        stage('DEPLOY') {
            steps {
                echo "DEPLOY SUCCESS"
            }
        }
    }
}
