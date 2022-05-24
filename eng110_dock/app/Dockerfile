# select base image to build our own customised node app microservice

FROM node

# set working directory 
WORKDIR /usr/src/app

# install node_modules
ADD package.json /usr/src/app/package.json

COPY package*.json ./

RUN npm install -g npm@latest

RUN npm install express

# define the port
COPY . . 
# start the app with CMD

CMD ["node", "app.js"]