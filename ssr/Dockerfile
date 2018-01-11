FROM alpine
LABEL maintainer="go-ignite"

RUN apk --update add --no-cache libsodium py-pip \
    && pip --no-cache-dir install https://github.com/shadowsocksr-backup/shadowsocksr/archive/3.1.2.zip \
    && rm -rf /var/cache/apk

EXPOSE 3389/tcp 3389/udp

WORKDIR /usr/bin/
ENTRYPOINT ["ssserver","-s","0.0.0.0","-p","3389","-O","auth_aes128_md5","-o","tls1.2_ticket_auth_compatible","-G","32","--fast-open"]
