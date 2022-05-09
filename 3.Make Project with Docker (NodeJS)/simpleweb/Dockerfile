# Specify a base image
FROM node:14-alpine

WORKDIR /usr/app

# Install some dependencies

# Making changes to index.js will not cause docker to redownload dependencies
COPY ./package.json ./ 
RUN npm install
COPY ./ ./

# Default command
CMD ["npm", "start"]

