# Base image
FROM node:7-alpine

# Set NPM Log Level to reduce output
ENV NPM_CONFIG_LOGLEVEL warn

# Set version numbers
ENV NODE_SASS_VERSION 4.5.3
ENV LERNA_VERSION 2.0.0-rc.5
ENV ANGULAR_CLI_VERSION 1.1.2
ENV PM2_VERSION 2.5.0

ENV API_PORT 0.0.0.0
ENV API_BASE_URL /

# Install global packages
RUN npm install -g \
  node-sass@${NODE_SASS_VERSION} \
  lerna@${LERNA_VERSION} \
  @angular/cli@${ANGULAR_CLI_VERSION} \
  pm2@${PM2_VERSION}

# Add application folder
RUN mkdir /app
WORKDIR /app

# Add package.json and install deps
ADD package.json /app/package.json
RUN npm install @angular/cli@${NGCLI_VERSION}
RUN npm install && npm cache clean
