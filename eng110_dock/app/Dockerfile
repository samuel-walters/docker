FROM node:alpine
WORKDIR /usr/src/app

#Set working directory
WORKDIR /usr/src/app
# Add packages
ADD package.json /usr/src/app/package.json
# Copy packages
COPY package*.json ./
# Install npm
RUN npm install -g npm@latest
# Run npm
RUN npm install express
# Copy everything from current working directory over to container's current working directory
COPY . . 
# Allow port 300
EXPOSE 3000
# Start the app
CMD ["node", "app.js"]