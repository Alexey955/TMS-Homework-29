pipeline {
    agent {
        label 'built-in' 
    }
    parameters {
        choice(name: 'Action', choices: ['Compose ps', 'Compose start', 'Compose stop'])
    }
    environment {
        TG_CHAT_ID = credentials('tg_chat_id')
        TG_TOKEN = credentials('tg_token')
    }
    stages {
        stage('Compose ps') {
            when {
                expression {params.Action == 'Compose ps'}
            }
            steps {
                    sh '''
                       #!/bin/bash
                   
                       CONTAINERS_STATS=$(docker-compose -p tms-lesson-24 ps -a --format "table {{.Name}}\t\t{{.Status}}")
                       CONTAINERS_STATS=$(echo "$CONTAINERS_STATS" | sed 's/+0000 UTC//g')

                       curl -X POST -H "Content-Type:multipart/form-data" -F "chat_id=$TG_CHAT_ID" -F "text=$CONTAINERS_STATS" "https://api.telegram.org/bot$TG_TOKEN/sendMessage"
                       '''
            }
        }
        stage('Compose stop') {
            when {
                expression {params.Action == 'Compose stop'}
            }
            steps {
                    sh '''
                       #!/bin/bash

                       docker-compose -p tms-lesson-24 stop
                   
                       CONTAINERS_STATS=$(docker-compose -p tms-lesson-24 ps -a --format "table {{.Name}}\t\t{{.Status}}")
                       CONTAINERS_STATS=$(echo "$CONTAINERS_STATS" | sed 's/+0000 UTC//g')

                       curl -X POST -H "Content-Type:multipart/form-data" -F "chat_id=$TG_CHAT_ID" -F "text=$CONTAINERS_STATS" "https://api.telegram.org/bot$TG_TOKEN/sendMessage"
                       '''
            }
        }
    }
}
