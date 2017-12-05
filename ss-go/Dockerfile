FROM alpine:latest
LABEL maintainer="go-ignite"

RUN apk --no-cache add wget && cd /
RUN wget https://github.com/shadowsocks/shadowsocks-go/releases/download/1.2.1/shadowsocks-server.tar.gz --no-check-certificate

RUN tar -zxvf shadowsocks-server.tar.gz \
			&& mv shadowsocks-server server \
			&& rm -rf shadowsocks-server.tar.gz \
			&& chmod +x server \
			&& apk del wget \
			&& rm -rf /var/cache/apk/*

EXPOSE 3389
ENTRYPOINT ["/server"]
