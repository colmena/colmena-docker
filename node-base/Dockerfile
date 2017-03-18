# Base image
FROM node:7.7.2-alpine

# Set version numbers
ENV PM2_VERSION 2.4.2
ENV NPS_VERSION 5.0.4

# Install global packages
RUN npm install -g nps@${NPS_VERSION}
RUN npm install -g pm2@${PM2_VERSION}

# Add application folder
RUN mkdir /app
WORKDIR /app

# Add package.json and install deps
ADD package.json /app/package.json
RUN npm install && npm cache clean

# Expose the listening port
EXPOSE 3000

# Start the server
CMD ["pm2-docker", "start", "process.yml"]
