pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'lscr.io/linuxserver/sonarr:latest'
        CONTAINER_NAME = 'sonarr'
        PUID = '1000'
        PGID = '1000'
        TZ = 'America/Monterrey'
        WEBUI_PORTS = '8989/tcp,8989/udp'
        CONFIG_PATH = '/home/docker/sonarr/config:/config'
        MEDIA_PATH = '/mnt/Media'
        TVSHOWS_PATH = '/mnt/Media/TVShows'
        MYSHOWS_PATH = '/mnt/Media/MyShows'
        MOVIES_PATH = '/mnt/Media/Movies'
        MYMOVIES_PATH = '/mnt/Media/MyMovies'
        DOWNLOADS_PATH = '/mnt/Media/Downloads'
        TVSDOWNLOADS_PATH = '/mnt/Media/TVShows/TVShowsDownloads'
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
                        -v ${MEDIA_PATH}:/Media \
                        -v ${DOWNLOADS_PATH}:/downloads \
                        -v ${TVSHOWS_PATH}:/TVShows \
                        -v ${MYSHOWS_PATH}:/MyShows \
                        -v ${MOVIES_PATH}:/Movies \
                        -v ${MYMOVIES_PATH}:/MyMovies \
                        -v ${TVSDOWNLOADS_PATH}:/TVShowsDownloads \
                        ${DOCKER_IMAGE}
                    """
                }
            }
        }
    }
}
