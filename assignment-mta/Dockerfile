FROM node:22-alpine3.20

RUN apk update && apk add --no-cache graphicsmagick

WORKDIR /app

COPY package*.json ./

RUN npm install && npm cache clean --force

COPY . .

ENV CHARCOAL_FACTOR=0.1

CMD [ "node", "index.js" ]
