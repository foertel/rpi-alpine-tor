# Tor 0.3.0.1-alpa - alpha version

FROM armhf/alpine:latest
MAINTAINER Felix Oertel "https://github.com/foertel"

EXPOSE 9050

RUN build_pkgs=" \
	openssl-dev \
	zlib-dev \
	libevent-dev \
	gnupg \
	" \
  && runtime_pkgs=" \
	build-base \
	openssl \
	zlib \
	libevent \
	" \
  && apk --update add ${build_pkgs} ${runtime_pkgs} \
  && cd /tmp \
  && wget https://www.torproject.org/dist/tor-0.4.4.4-rc.tar.gz \
  && tar xzf tor-0.4.4.4-rc.tar.gz \
  && cd /tmp/tor-0.4.4.4-rc \
  && ./configure \
  && make -j6 \
  && make install \
  && cd \
  && rm -rf /tmp/* \
  && apk del ${build_pkgs} \
  && rm -rf /var/cache/apk/*

RUN adduser -Ds /bin/sh tor

RUN mkdir /etc/tor
COPY torrc /etc/tor/

USER tor
CMD ["tor", "-f", "/etc/tor/torrc"]
