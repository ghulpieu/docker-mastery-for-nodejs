# a base stage for all future stages
# with only prod dependencies and
# no code yet
FROM node:18-slim AS base
ENV NODE_ENV=production
WORKDIR /app
COPY package*.json ./
RUN npm ci \
    && npm cache clean --force
ENV PATH /app/node_modules/.bin:$PATH

# a dev and build-only stage. we don't need to
# copy in code since we bind-mount it
FROM base AS dev
ENV NODE_ENV=development
RUN npm install
CMD ["/app/node_modules/.bin/nodemon"]

FROM dev AS build
COPY . .
RUN tsc
# you would also run your tests here

# this only has minimal deps and files
FROM base AS prod
COPY --from=build /app/dist/ .
CMD ["node", "app.js"]
