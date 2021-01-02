FROM alpine:3.12.3

RUN apk add --no-cache --purge -uU cgit lighttpd git \
    && echo 'include "cgit.conf"' >> /etc/lighttpd/lighttpd.conf

EXPOSE 80

COPY cgit.conf /etc/lighttpd/cgit.conf
COPY cgitrc /etc/cgitrc

VOLUME ["/var/repositories"]

CMD lighttpd -D -f /etc/lighttpd/lighttpd.conf