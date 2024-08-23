FROM node:10-slim

EXPOSE 3000

USER node

WORKDIR /node

COPY --chown=node:node  package*.json ./

RUN npm install && npm cache clean --force

WORKDIR /node/app

COPY --chown=node:node . .

CMD ["node", "app.js"]
