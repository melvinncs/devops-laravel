pipeline {
    agent any

    stages {
        stage('Deploy') {
            steps {
                script {
                    docker.image('agung3wi/alpine-rsync:1.1').inside {
                        sshagent(['ssh-pwd']) {
                            sh 'echo Deploy Success'
                        }
                    }
                }
            }
        }
    }
}