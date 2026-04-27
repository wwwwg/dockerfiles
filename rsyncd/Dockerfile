ARG OS_VER=latest

FROM alpine:${OS_VER}

RUN set -ex; \
    sed -i 's/dl-cdn\.alpinelinux\.org/mirrors.ustc.edu.cn/g' /etc/apk/repositories; \
    apk add --no-cache rsync

RUN ln -sf /dev/stdout /var/log/rsyncd.log

VOLUME /config

EXPOSE 873/tcp

ENTRYPOINT ["/usr/bin/rsync"]

CMD ["--daemon", "--no-detach", "--config=/config/rsyncd.conf"]
