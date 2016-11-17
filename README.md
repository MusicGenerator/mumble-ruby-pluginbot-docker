## Mumble-Ruby-Pluginbot
This is a dockerized music bot named [Mumble-Ruby-Pluginbot](https://github.com/dafoxia/mumble-ruby-pluginbot). It contains the bot itself and a MPD server.

The bot uses the current devel branch with many new features compared to the master branch.

## Todo
Decide whether or not to expose 7701 to be able to control the MPD. If so we need to change mpd config to allow non localhost access.

## ENV variabled
See Dockerfile for all variables.

## Volumes
You need to specify the volumes "/home/botmaster/music" and "/home/botmaster/temp".

## Build it
```
    docker build -t mumblerubypluginbot .
```

## Running the Bot

```
    docker run -d -t --name bot1 \ 
     -v /somehostfolder/music:/home/botmaster/music \
     -v /somehostfolder/temp:/home/botmaster/temp \ 
     -v /somehostfolder/certs:/home/botmaster/certs \ 
     -e MUMBLE_USERNAME="MRPB_Docker_BOT" \ 
     -e MUMBLE_BITRATE="60000" \ 
     -e MUMBLE_HOST="m.natenom.com" \ 
     -e MUMBLE_PORT="64738" \ 
     -e MUMBLE_CHANNEL="Bottest" \ 
     -e MUMBLE_PASSWORD="supersecretpw" \ 
     mumblerubypluginbot
```

If you omit all -e variables the bot connects to m.natenom.com.

## Playlists, state
The playlists are stored within the container, not in the volumes.
