pipeline {
    agent any

    environment {
        USERNAME = sh(script: 'echo $USER', returnStdout: true).trim()
        DOCKER_IMAGE = 'lscr.io/linuxserver/sonarr:latest'
        CONTAINER_NAME = 'sonarr'
        PUID = '1000'
        PGID = '1000'
        TZ = 'America/Monterrey'
        WEBUI_PORTS = '8989/tcp,8989/udp'
        CONFIG_PATH = '/home/docker/sonarr/config'
    }

    stages {
        stage('Deploy Docker Image') {
            steps {
                script {
                    sh """                      
                    docker run -d \
                        --restart always \
                        --name ${CONTAINER_NAME} \
                        -p 8989:8989 \
                        -e PUID=${PUID} \
                        -e PGID=${PGID} \
                        -e TZ=${TZ} \
                        -v ${CONFIG_PATH}:/config \
                        -v /media/${USERNAME}/Media:/Media \
                        -v /media/${USERNAME}/Media/Downloads:/downloads \
                        -v /media/${USERNAME}/Media/TVShows:/TVShows \
                        -v /media/${USERNAME}/Media/MyTVShows:/MyTVShows \
                        ${DOCKER_IMAGE}
                    """
                }
            }
        }
    }
}
