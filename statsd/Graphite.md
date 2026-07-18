# Links

- [Web site](https://graphite.readthedocs.io/en/latest/index.html#)
- The [Graphite Docker repo](https://github.com/graphite-project/docker-graphite-statsd)

# [Install](https://graphite.readthedocs.io/en/latest/install.html#)

1. [Install Docker](../Docker.md#install)
1. Download the Graphite image to make sure it exists: `sudo docker pull graphiteapp/graphite-statsd`
   Technically it is not necessary because running a container will download an image, but better to separate two distinct tasks
1. Confirm that the image was downloaded: `sudo docker images`

# Configure

- [Default Port configuration](https://github.com/graphite-project/docker-graphite-statsd?tab=readme-ov-file#mapped-ports)

1. Configure router to allow inbound UDP packets to the Graphite StatsD port.

# Run

1. Startup the Graphite container:

```
sudo docker run -d\
 --name graphite\
 --restart=always\
 -p 80:80\
 -p 2003-2004:2003-2004\
 -p 2023-2024:2023-2024\
 -p 8125:8125/udp\
 -p 8126:8126\
 graphiteapp/graphite-statsd
```

2. Confirm that it started up: `sudo docker stats`
3. Run the metrics load on Graphite server: `while true; do echo -n "example:$((RANDOM % 100))|c" | nc -w 1 -u 127.0.0.1 8125; done`
4. Check out the Graphite Web: http://<GRAPHITE_SERVER_IP>:80

# Clean

1. [Access the Graphite Docker container](../Docker.md#containers).
1. Navigate to the Graphite Whisper storage directory: `cd /opt/graphite/storage/whisper`
1. Remove unwanted metrics, they are usually under the `statsd` and `statsd_count` directories.
1. [Restart the Graphite Docker container](../Docker.md#containers).
