# Base image
FROM node:8-alpine

# Set NPM Log Level to reduce output
ENV NPM_CONFIG_LOGLEVEL warn

# Set version numbers
ENV NODE_GYP_VERSION 3.6.2
ENV NODE_SASS_VERSION 4.5.3
ENV LERNA_VERSION 2.4.0
ENV ANGULAR_CLI_VERSION 1.4.9
ENV PM2_VERSION 2.7.2

ENV SYSTEM_DEPS git
RUN apk update \
    && apk add --no-cache ${SYSTEM_DEPS}

ENV TEMP_DEPS g++ gcc libgcc libstdc++ linux-headers make python

# Install global packages
RUN apk update \
    && apk add --virtual native-deps --no-cache ${TEMP_DEPS} \
    && yarn add -g \
        @angular/cli@${ANGULAR_CLI_VERSION} \
        lerna@${LERNA_VERSION} \
        node-sass@${NODE_SASS_VERSION} \
        node-gyp@${NODE_GYP_VERSION} \
        pm2@${PM2_VERSION} \
    && apk del native-deps

# Install PhantomJS
ENV PHANTOM_VERSION 2.11
ENV PHANTOM_URL https://github.com/Overbryd/docker-phantomjs-alpine/releases/download/${PHANTOM_VERSION}/phantomjs-alpine-x86_64.tar.bz2
ENV PHANTOM_DEPS fontconfig curl
ENV PHANTOM_TARGET /usr/share

RUN apk update \
    && apk add --virtual phantom-virtual --no-cache ${PHANTOM_DEPS} \
    && mkdir -p ${PHANTOM_TARGET} \
    && cd ${PHANTOM_TARGET} \
    && curl -L ${PHANTOM_URL} | tar xj \
    && ln -s ${PHANTOM_TARGET}/phantomjs/phantomjs /usr/bin/phantomjs \
    && phantomjs --version \
    && apk del phantom-virtual

# Add application folder
RUN mkdir /app
WORKDIR /app
