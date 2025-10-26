pipeline {
    agent {
        label 'built-in' 
    }
    stages {
        stage('Выполнение на мастере') {
            steps {
                withCredentials([string(credentialsId: 'tg_chat_id', variable: 'TG_CHAT_ID')]) {
                    sh '''
                       #!/bin/bash
                   
                       CONTAINERS_STATS=$(docker-compose -p task_02 ps -a --format "table {{.Name}}\t\t{{.Status}}")
                       CONTAINERS_STATS=$(echo "$CONTAINERS_STATS" | sed 's/+0000 UTC//g')

                       curl -X POST -H "Content-Type:multipart/form-data" -F "chat_id='$TG_CHAT_ID'" -F "text=$CONTAINERS_STATS" "https://api.telegram.org/bot8056400841:AAH89GMWq-rb5d-NBxI7RBoRVe8s4o0mEX4/sendMessage"
                       '''
                }
            }
        }
    }
}
