### Alpine Linux Tor for Raspberry Pi

A lightweight [Tor][tor] [Docker image][dockerhub_project] built from source atop [Alpine Linux][alpine_linux] for Raspberry Pi. Available on [GitHub][github_project].

#### Usage

````bash
# Open up a Tor SOCKS proxy for use on the Raspberry Pi
$ docker run -p 127.0.0.1:9050:9050 foertel/rpi-alpine-tor
# To open the proxy for your local network, just bind it to the local IP of your Pi
$ docker run -p 192.168.0.17:9050:9050 foertel/rpi-alpine-tor
# Use your own torrc
$ vim tor/torrc
$ docker run -v $(pwd)/tor:/etc/tor:ro foertel/rpi-alpine-tor
````

#### Do not take my word for it

When it comes to security and encryption, you propably should not trust some guy of the internet. So instead of pulling the built image from the hub, clone the [GitHub Repository][github_project], check the Dockerfile and build your own container. Compiling will take some time, about 15 Minutes on a Raspberry Pi 2. But it's easy!

````bash
$ git clone https://github.com/foertel/rpi-alpine-tor
$ cd rpi-alpine-tor
$ docker build -t tor .
$ docker run -p 127.0.0.1:9050:9050 tor
````

#### Branches
##### stable

> Tor 0.2.9.8 (git-01ab67e38b358ae9) running on Linux with Libevent 2.0.22-stable, OpenSSL 1.0.2j and Zlib 1.2.8.

- `0.2.9.8`, `stable`, `latest` (2017-01-23, [Dockerfile](https://github.com/foertel/rpi-alpine-tor/tree/master/versions/0.2.9.8/Dockerfile), [Changes][tor_changes])

#### alpha

> Tor 0.3.0.1-alpha (git-ac04fcd2e758c225) running on Linux with Libevent 2.0.22-stable, OpenSSL 1.0.2j and Zlib 1.2.8.

- `0.3.0.1-alpha`, `alpha` (2017-01-23, [Dockerfile](https://github.com/foertel/rpi-alpine-tor/tree/master/versions/0.3.0.1-alpha/Dockerfile), [Changes][tor_alpha_changes])

### History

- 2017-01-23 - Initial version with Tor 0.2.9.8, 0.3.0.1-alpha and Alpine Linux 3.4.5 (OpenSSL 1.0.2j, gcc 5.3.0).

[alpine_linux]:        https://hub.docker.com/r/armhf/alpine/
[dockerhub_project]:   https://hub.docker.com/r/foertel/rpi-alpine-tor/
[github_project]:      https://github.com/foertel/rpi-alpine-tor/
[tor]:                 https://torproject.org/
[tor_changes]:         https://gitweb.torproject.org/tor.git/plain/ReleaseNotes?id=tor-0.2.9.8
[tor_alpha_changes]:   https://gitweb.torproject.org/tor.git/plain/ChangeLog
