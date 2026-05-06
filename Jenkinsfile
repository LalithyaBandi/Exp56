pipeline {
    agent any

    triggers {
        pollSCM('H/5 * * * *')
        cron('H 0 * * *')
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh '''
                mkdir -p bin
                javac -d bin src/App.java
                javac -d bin -cp bin test/AppTest.java
                '''
            }
        }

        stage('Run') {
            steps {
                sh '''
                java -cp bin App
                java -cp bin AppTest
                '''
            }
        }
    }
}
