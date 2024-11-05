FROM node:lts-alpine3.20 AS build

WORKDIR /app

COPY . .

RUN npm install && \
    npm run build

FROM node:lts-alpine3.20 AS production

WORKDIR /app

COPY --from=build /app/.next/standalone/ .
COPY --from=build /app/.next/static/ ./.next/static/

ENTRYPOINT [ "node", "server.js" ]