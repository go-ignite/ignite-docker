FROM ubuntu:16.04 as builder

RUN apt-get update \
			&& apt-get install -y --no-install-recommends build-essential autoconf libtool libssl-dev libpcre3-dev asciidoc xmlto git
RUN git config --global http.sslVerify false \
			&& git clone --branch 2.4.1 --depth 1 https://github.com/shadowsocksr-backup/shadowsocksr-libev.git /shadowsocksr-libev
WORKDIR /shadowsocksr-libev
RUN ./configure \
 && make \
 && make install

FROM ubuntu:16.04
LABEL maintainer="go-ignite"
run apt-get update \
			&& apt-get install -y --no-install-recommends libssl1.0.0 \
			&& rm -rf /var/lib/apt/lists/*

COPY --from=builder /usr/local/bin/ss-server /server

EXPOSE 3389
ENTRYPOINT ["/server","-p","3389"]
