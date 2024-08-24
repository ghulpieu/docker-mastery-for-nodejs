# fill in the blanks to dockerize this node app
FROM node:22-alpine3.19

EXPOSE 3000

RUN apk update && apk add --no-cache tini

USER node

WORKDIR /var/www

COPY --chown=node:node package.json package-lock*.json ./

RUN npm install && npm cache clean --force

COPY --chown=node:node . .

# tini handles the init process for us
# note that tini is in docker by default, use --init
# ENTRYPOINT [ "/sbin/tini", "--" ]

CMD [ "node", "./app.js" ]
