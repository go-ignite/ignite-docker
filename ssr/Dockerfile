FROM alpine
LABEL maintainer="go-ignite" version="3.2.2" org.label-schema.url="https://github.com/go-ignite"

RUN apk --update add --no-cache libsodium py-pip \
    && pip --no-cache-dir install https://github.com/shadowsocksrr/shadowsocksr/archive/3.2.2.zip \
    && rm -rf /var/cache/apk

EXPOSE 3389/tcp 3389/udp

WORKDIR /usr/bin/
ENTRYPOINT ["ssserver","-s","0.0.0.0","-p","3389","-O","auth_aes128_md5","-o","tls1.2_ticket_auth_compatible","-G","32","--fast-open"]
