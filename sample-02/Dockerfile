FROM node:10-alpine

RUN apk add --update curl

EXPOSE 3000

WORKDIR /usr/src/app

# copy into current working directory
# * means copy if file exists
COPY package.json package-lock.json* ./

RUN npm install && npm cache clean --force

COPY . .

CMD [ "node", "./bin/www" ]
