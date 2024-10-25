FROM node

WORKDIR /app

COPY package.json /app 


# install packages 
RUN npm install

# COPY . .
COPY . /app

EXPOSE 80

# RUN node server.js
CMD [ "node","server.js" ]