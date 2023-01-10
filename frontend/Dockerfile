FROM node:16

WORKDIR /usr/app

COPY package.json .

RUN npm i --quiet

COPY . .

RUN npm install pm2 -g

CMD ["node", "index.js"]
