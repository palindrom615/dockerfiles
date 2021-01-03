FROM alpine:3.12.3

RUN apk add --no-cache --purge -uU cgit lighttpd git lua5.3 lua5.3-dev lua5.3-posix lua5.3-ossl \
    py3-pygments py3-markdown py3-docutils \
    && echo 'include "cgit.conf"' >> /etc/lighttpd/lighttpd.conf \
    && mkdir -p /var/cache/cgit

EXPOSE 80

COPY cgit.conf /etc/lighttpd/cgit.conf
COPY cgitrc /etc/cgitrc

VOLUME ["/etc/cgitrc.d", "/var/repositories", "/var/lib/cgit", "/usr/share/webapps/cgit/static"]

CMD lighttpd -D -f /etc/lighttpd/lighttpd.conf
