FROM node:20 AS dev

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 3001

CMD ["npm", "run", "dev"]

FROM node:20-slim AS prod

WORKDIR /app

COPY package*.json ./

RUN npm install --omit=dev

COPY . .

ENV NODE_ENV=production

RUN chown -R node:node /app

USER node

EXPOSE 3001

CMD ["npm", "start"]