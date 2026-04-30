ARG OS_VER=latest

FROM alpine:${OS_VER}

ARG PGID=1000 PUID=1000

RUN set -eux; \
    addgroup -g ${PGID} git; \
    adduser -D -h /data -s /usr/bin/git-shell -u ${PUID} -G git git; \
    passwd -u git; \
    apk add --no-cache git openssh-server; \
    ssh-keygen -A >/dev/null

EXPOSE 22/tcp

ENTRYPOINT ["/usr/sbin/sshd"]

CMD ["-D", "-o", "AllowUsers=git", "-o", "PasswordAuthentication=no", "-o", "PrintMotd=no"]
