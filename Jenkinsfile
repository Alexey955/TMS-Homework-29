pipeline {
    agent {
        label 'built-in' 
    }
    stages {
        stage('Выполнение на мастере') {
            steps {
                sh 'echo "Я выполняюсь на мастере!"'
                sh 'pwd'
            }
        }
    }
}
