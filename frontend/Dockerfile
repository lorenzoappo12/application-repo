FROM node:16

WORKDIR /usr/app

COPY package.json .

RUN npm i --quiet

COPY . .

RUN npm install

CMD ["node", "index.js"]
