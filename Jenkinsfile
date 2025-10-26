pipeline {
    agent {
        label 'built-in' 
    }
    stages {
        stage('Выполнение на мастере') {
            steps {
                sh '''
                   #!/bin/bash
                   
                   CONTAINERS_STATS=$(docker-compose -p task_02 ps -a --format "table {{.Name}}\t\t{{.Status}}")
                   CONTAINERS_STATS=$(echo "$CONTAINERS_STATS" | sed 's/+0000 UTC//g')

                   curl -X POST -H "Content-Type:multipart/form-data" -F "chat_id={ params.tg_chat_id }" -F "text=$CONTAINERS_STATS" "https://api.telegram.org/bot8056400841:AAH89GMWq-rb5d-NBxI7RBoRVe8s4o0mEX4/sendMessage"
                '''
            }
        }
    }
}
