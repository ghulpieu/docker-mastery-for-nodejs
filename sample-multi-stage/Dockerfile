# docker buildx b --target=<stage> -t multi-stage:<stage> .
#

# Stage prod
FROM node:18-slim AS prod
ENV NODE_ENV=production
WORKDIR /app

COPY package.json package-lock*.json ./
RUN npm ci --omitdev && npm cache clean --force
COPY . .

CMD [ "node", "./bin/www" ]

# Stage dev
FROM prod AS dev
ENV NODE_ENV=development

RUN npm install && npm cache clean --force

CMD [ "node_modules/nodemon/bin/nodemon.js", "./bin/www", "--inspect=0.0.0.0:9229" ]

# Stage test
FROM dev AS test
ENV NODE_ENV=development

CMD [ "npm", "test" ]
