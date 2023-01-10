FROM node:16

#EXPOSE 3000


#WORKDIR /usr/app

COPY package.json .

#RUN npm i --quiet

#COPY . .

RUN npm ci
RUN npm start

#RUN npm install

#CMD ["node", "src/index.js"]
