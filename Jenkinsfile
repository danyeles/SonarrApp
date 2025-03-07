
sudo docker run -d \
--name=radarr \
  --restart unless-stopped \
-v /home/docker/radarr/config:/config \
-v /mnt/Media:/Media \
-v /mnt/Media/Downloads:/downloads \
-v /mnt/Media/Movies:/Movies \
-v /mnt/Media/Movies/MoviesDownloads:/MoviesDownloads \
-v /mnt/Media/MyMovies:/MyMovies \
-e PGID=1000 \
-e PUID=1000 \
-e TZ=America/Monterrey \
-p 7878:7878 \
linuxserver/radarr:latest



sudo docker run -d \
  --name=sonarr \
  -e PUID=1000 \
  -e PGID=1000 \
  -e TZ=America/Monterrey \
  -p 8989:8989 \
  -v /home/docker/sonarr/config:/config \
  -v /mnt/Media:/Media \
  -v /mnt/Media/Downloads:/downloads \
  -v /mnt/Media/TVShows:/TVShows \
  -v /mnt/Media/TVShows/TVShowsDownloads:/TVShowsDownloads \
  -v /mnt/Media/MyShows:/MyShows \
  --restart unless-stopped \
  lscr.io/linuxserver/sonarr:latest
