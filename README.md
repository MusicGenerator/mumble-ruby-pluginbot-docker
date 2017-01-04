## Mumble-Ruby-Pluginbot-Docker
This is a dockerized music bot named [Mumble-Ruby-Pluginbot](https://github.com/MusicGenerator/mumble-ruby-pluginbot). It contains the bot itself and an MPD server.

The bot uses the current devel branch with many new features compared to the master branch.

## Debian or Ubuntu?
This dockerfile works both with Debian and Ubuntu. It was originally created for Debian but then changed a little to work with Ubuntu also because Ubuntu uses a more recent version of MPD. If you experience problems where the bot disconnects when handling radio streams you should use Ubuntu as an image, see first line of the Dockerfile.

The default is Ubuntu though.

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
"/home/botmaster/mpd1/playlists/"

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
     -v /somehostfolder/playlists:/home/botmaster/mpd1/playlists/ \
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
The Dockerfile is mainly a script made from the documentation you can find at http://mumble-ruby-pluginbot.readthedocs.io/en/master/installation_howto.html.

## Docker commands for the bot
### Watching the log

    docker exec -t -i container_name tail -n1 -f /home/botmaster/logs/bot1.log

### FIXME...
