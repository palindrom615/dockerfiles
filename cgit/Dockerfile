FROM alpine:3.12.3

RUN apk add --no-cache --purge -uU cgit lighttpd lua5.3-posix lua5.3-ossl highlight \
    py3-pygments py3-markdown py3-docutils \
    && echo 'include "cgit.conf"' >> /etc/lighttpd/lighttpd.conf

EXPOSE 80

COPY cgit.conf /etc/lighttpd/cgit.conf
COPY cgitrc /etc/cgitrc
COPY filters/syntax-highlighting.sh /usr/lib/cgit/filters
RUN chmod +x /usr/lib/cgit/filters/syntax-highlighting.sh
COPY cgit.css /usr/share/webapps/cgit

VOLUME ["/etc/cgitrc.d", "/var/repositories", "/var/lib/cgit", "/usr/share/webapps/cgit/static"]

CMD lighttpd -D -f /etc/lighttpd/lighttpd.conf
