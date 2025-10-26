pipeline {
    agent {
        label 'built-in' 
    }
    stages {
        stage('Выполнение на мастере') {
            steps {
                sh '''
                   #!/bin/bash
                   
                   CONTAINERS_STATS=$(docker-compose -p task_02 ps --format "table {{.Name}}\t\t{{.Status}}\t\t{{.CreatedAt}}")
                   echo $CONTAINERS_STATS

                   curl -X POST -H "Content-Type:multipart/form-data" -F "chat_id=782298795" -F "text=$CONTAINERS_STATS" "https://api.telegram.org/bot8056400841:AAH89GMWq-rb5d-NBxI7RBoRVe8s4o0mEX4/sendMessage"
                '''
            }
        }
    }
}
