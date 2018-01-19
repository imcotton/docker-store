
FROM gradle:jdk8-alpine


LABEL maintainer="Cotton H."
LABEL version="1.0"
LABEL description="JDK Gradle Node.js CHROME_BIN based on Alpine distro"


USER root


RUN echo start \
\
    && EDGE='http://dl-cdn.alpinelinux.org/alpine/edge' \
    && REPO='/etc/apk/repositories' \
\
    && echo "$EDGE/main" >> $REPO \
    && echo "$EDGE/community" >> $REPO \
    && sed -i 's#http\://dl-cdn.alpinelinux.org#https\://alpine.global.ssl.fastly.net#g' $REPO \
\
    && apk add --no-cache --virtual .build-deps \
            curl           \
            perl           \
            gnupg          \
            git            \
            nodejs         \
            nodejs-npm     \
            chromium       \
\
    && rm -rf /var/cache/apk/* /tmp/* \
\
&& echo end



ENV CHROME_BIN=/usr/bin/chromium-browser

