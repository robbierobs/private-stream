Private Live Streaming
======================

These instructions allow you to run a live stream via docker containers and OBS

# Server Setup

In this guide we'll be using a Ubuntu 20.04 server to host the live stream.

1. Open ports 1935 on your firewall/gateway to allow traffic in and out to public addresses

2. On the server, pull the docker image for nginx-rtmp
    `docker pull tiangolo/nginx-rtmp`
3. Run the docker container with the following command
    `docker run -d -p 1935:1935 --name nginx-rtmp tiangolo/nginx-rtmp`
4. If you are running this publicly, you'll need your public IP.
    `curl ifconfig.me`

# Client Setup

1. Download and install OBS

2. Set the stream address to your server address with the `/live` path. This is not unique and you can change the name of it if you'd like. For simplicity, leave the stream key blank.
    `192.168.x.x:1935/live`
3. Set up OBS how you'd like for capture and audio.

4. Click "Start Streaming"

# Viewing the Stream

We're going to use VLC to view the stream.

1. Download and install VLC.

2. Navigate to "Media -> Open Network Stream"

3. Enter the URL for the server you created earlier, with the procotol, IP and port.
    Private
    `rtmp://192.168.x.x:1935/live`
    Public
    `rtmp://<public ip address>:1935/live`
