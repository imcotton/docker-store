
FROM node:8-alpine AS node


LABEL maintainer="Cotton H."
LABEL version="1.0"
LABEL description="JDK Gradle Node.js CHROME_BIN based on Alpine distro"





FROM gradle:jdk8-alpine

USER root

WORKDIR /usr/local/bin/


COPY --from=node /usr/local/bin/node   ./
COPY --from=node /usr/local/lib/node_modules   ../lib/node_modules

RUN ln -s ../lib/node_modules/npm/bin/npm-cli.js   npm &&\
    ln -s ../lib/node_modules/npm/bin/npx-cli.js   npx


WORKDIR /


ARG MIRROR

RUN echo start \
\
    && EDGE='http://dl-cdn.alpinelinux.org/alpine/edge' \
    && REPO='/etc/apk/repositories' \
\
    && echo "$EDGE/main" >> $REPO \
    && echo "$EDGE/community" >> $REPO \
    && sed -i "s|http://dl-cdn.alpinelinux.org|${MIRROR:-https://alpine.global.ssl.fastly.net}|g" $REPO \
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

