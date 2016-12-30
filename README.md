## Mumble-Ruby-Pluginbot-Docker
This is a dockerized music bot named [Mumble-Ruby-Pluginbot](https://github.com/MusicGenerator/mumble-ruby-pluginbot). It contains the bot itself and an MPD server.

The bot uses the current devel branch with many new features compared to the master branch.

## Ports
Port 7701 is exposed.

Use for example "-p 127.0.0.1:7701:7701" to bind it to localhost inside of the host only.


## ENV variabled
See Dockerfile for all variables.

## Volumes
You need to specify the volumes:
"/home/botmaster/music"
"/home/botmaster/temp"
"/home/botmaster/certs"

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

If you omit all -e variables the bot connects to m.natenom.com into our Bottest channel.

## Configure mumble-ruby-pluginbot
See conf/override_config.yml which is an override config. That means you only need to add settings you want to be overwritten.

## Configure mpd
See conf/mpd.conf which is the complete configuration file.

## Playlists, state
The playlists are stored within the container, not in the volumes.

## Notes
The Dockerfile is mainly a script made from the documentation you can find at http://mumble-ruby-pluginbot.readthedocs.io/en/latest/installation_howto.html.
