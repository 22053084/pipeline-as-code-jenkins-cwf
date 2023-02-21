pipeline {
    agent any
    stages {
        stage('S1_22053084') {
            steps {
                echo 'S1_22053084 : Environment Preparation Completed'
            }
        }
        stage('S2_22053084') {
            steps {
                sh '''
                    docker rm -f S2_22053084_Server
                    docker run -d --name S2_22053084_Server -p 42000:80 22053084_webimage
                '''
                echo 'S2_22053084 : Web Server Creation Completed'
            }
        }
        stage('S3_22053084') {
            steps {
                echo 'S3_22053084 : API Test Completed'
            }
        }
        stage('S4_22053084') {
            steps {
                echo 'S4_22053084 : DAST Security Test Completed'
            }
        }
        stage('S5_22053084') {
            steps {
                echo 'Do you want to release the work?'
            }
        }
        stage('S6_22053084') {
            steps {
                input message: 'Do you want to release the work?', ok: 'Y', submitter: 'Release'
                if (input == 'Y') {
                    echo 'Work Released - 22053084'
                } else {
                    abort
                }
            }
        }
    }
}
