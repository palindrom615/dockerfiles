FROM alpine:3.12.3

RUN apk add --no-cache --purge -uU cgit lighttpd git lua5.3 lua5.3-dev lua5.3-posix lua5.3-ossl \
    py3-pygments py3-markdown py3-docutils \
    && echo 'include "cgit.conf"' >> /etc/lighttpd/lighttpd.conf \
    && mkdir -p /var/cache/cgit

EXPOSE 80

COPY cgit.conf /etc/lighttpd/cgit.conf

VOLUME ["/etc/cgitrc", "/var/repositories", "/var/lib/cgit"]

CMD lighttpd -D -f /etc/lighttpd/lighttpd.conf