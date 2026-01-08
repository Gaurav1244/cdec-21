pipeline {
    agent any

    stages {

        stage('PULL') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Gaurav1244/cdec-21.git'
            }
        }

        stage('BUILD') {
            steps {
                dir('backend') {
                    sh 'mvn clean package -DskipTests'
                }
            }
        }

        stage('SONARQUBE ANALYSIS') {
            steps {
                withSonarQubeEnv('mysonarqube') {
                    dir('backend') {
                        sh '''
                        mvn clean verify sonar:sonar \
                         -Dsonar.projectKey=myapp \
                         -Dsonar.projectName='myapp' \
                        '''
                    }
                }
            }
        }

        stage('DEPLOY') {
            steps {
                echo "DEPLOY SUCCESS"
            }
        }
    }
}

