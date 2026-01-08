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
                        mvn org.sonarsource.scanner.maven:sonar-maven-plugin:sonar \
<<<<<<< HEAD
                          -Dsonar.projectKey=myapp \
                          -Dsonar.projectName=myapp
=======
                          -Dsonar.projectKey=MySonarQube \
                          -Dsonar.projectName=MySonarQube
>>>>>>> 28c9a0e906c745221dd89de18ca05216f88a5d0a
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

