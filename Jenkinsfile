pipeline {
    agent {
        label 'built-in' 
    }
    stages {
        stage('Выполнение на мастере') {
            steps {
                sh 'docker-compose -p task_02 ps'
            }
        }
    }
}
