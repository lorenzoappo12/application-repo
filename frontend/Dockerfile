FROM node:16

WORKDIR /app
COPY package.json /app
RUN npm ci && npm start
COPY . /app
CMD node index.js
EXPOSE 3000
