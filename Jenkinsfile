pipeline {
    agent any

    stages {
        stage('initialize') {
            steps {
                cleanWs()
            }
        }
        stage('w/o docker') {
            steps {
                sh '''
                    echo start w/o docker
                    echo "some text 1" >> file1.txt
                    ls -la
                    echo stop w/o docker
                '''
            }
        }
        stage('w docker') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    echo start w/ docker
                    echo "some text 2" >> file2.txt
                    ls -la
                    node --version
                    npm --version
                    echo end  w/ docker
                '''
            }
        }
    }
}
