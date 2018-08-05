
ARG NV=8
FROM node:${NV}-alpine


LABEL maintainer="Cotton H."
LABEL version="1.0"
LABEL description="Node.js v8 with CHROME_BIN based on Alpine distro"


RUN echo start \
\
    && EDGE='http://dl-cdn.alpinelinux.org/alpine/v3.8' \
    && REPO='/etc/apk/repositories' \
\
    && echo "$EDGE/main" >> $REPO \
    && echo "$EDGE/community" >> $REPO \
    && sed -i 's|http://dl-cdn.alpinelinux.org|https://alpine.global.ssl.fastly.net|g' $REPO \
\
    && apk add --no-cache --virtual .build-deps \
            curl           \
            perl           \
            gnupg          \
            git            \
            chromium       \
\
    && rm -rf /var/cache/apk/* /tmp/* \
\
&& echo end



ENV CHROME_BIN=/usr/bin/chromium-browser

