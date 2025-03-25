pipeline {
    agent any

    environment {
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
                        -v /media/Media:/Media \
                        -v /media/Media/Downloads:/downloads \
                        -v /media/Media/TVShows:/TVShows \
                        -v /media/Media/MyTVShows:/MyTVShows \
                        ${DOCKER_IMAGE}
                    """
                }
            }
        }
    }
}
