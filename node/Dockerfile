# Set the base image to Ubuntu
FROM node:boron

# File Author / Maintainer
MAINTAINER Kareem Saleh

# Install Node.js and other dependencies
#RUN apt-get update && \
#    apt-get -y install curl && \
#    curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash - && \
#    sudo apt-get install -y build-essential nodejs


# Install nodemon
RUN npm install -g nodemon
RUN npm install express --save
RUN npm install redis --save

# Provides cached layer for node_modules
ADD package.json /tmp/package.json
RUN cd /tmp && npm install
RUN mkdir -p /src && cp -a /tmp/node_modules /src/

# Define working directory
WORKDIR /src
ADD . /src

# Expose port
EXPOSE 8080

# Run app using nodemon
CMD ["nodemon", "/src/index.js"]
