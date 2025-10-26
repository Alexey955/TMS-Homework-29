pipeline {
    agent {
        label 'built-in' 
    }
    stages {
        stage('Выполнение на мастере') {
            steps {
                sh 'docker ps -a'
            }
        }
    }
}
