# Base image
FROM node:7-alpine

# Set NPM Log Level to reduce output
ENV NPM_CONFIG_LOGLEVEL warn

# Set version numbers
ENV NODE_GYP_VERSION 3.6.2
ENV NODE_SASS_VERSION 4.5.3
ENV LERNA_VERSION 2.0.0-rc.5
ENV ANGULAR_CLI_VERSION 1.1.3
ENV PM2_VERSION 2.5.0

# Install global packages
RUN npm install -g \
  node-gyp@${NODE_GYP_VERSION} \
  node-sass@${NODE_SASS_VERSION} \
  lerna@${LERNA_VERSION} \
  @angular/cli@${ANGULAR_CLI_VERSION} \
  pm2@${PM2_VERSION}

ENV PHANTOM_VERSION 2.11

# Install PhantomJS
RUN apk update && apk add --no-cache fontconfig git curl && \
  mkdir -p /usr/share && \
  cd /usr/share \
  && curl -L https://github.com/Overbryd/docker-phantomjs-alpine/releases/download/${PHANTOM_VERSION}/phantomjs-alpine-x86_64.tar.bz2 | tar xj \
  && ln -s /usr/share/phantomjs/phantomjs /usr/bin/phantomjs \
  && phantomjs --version

# Add application folder
RUN mkdir /app
WORKDIR /app
