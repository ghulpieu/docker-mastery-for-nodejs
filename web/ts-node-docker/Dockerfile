FROM node:22.7.0 AS base

# ARG captures env argument passed from compose file
ARG NODE_ENV
ENV NODE_ENV=development

WORKDIR /home/node/app

COPY package*.json ./

RUN npm install && npm cache clean --force

COPY . .

FROM base AS production

ENV NODE_PATH=./build

RUN npm run build
