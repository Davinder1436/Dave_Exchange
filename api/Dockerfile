
FROM node:20-alpine AS build

WORKDIR /usr/src/exchange/api/

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build

FROM node:20-alpine
WORKDIR /usr/src/exchange/api
COPY --from=build /usr/src/exchange/api/dist ./dist
COPY --from=build /usr/src/exchange/api/node_modules ./node_modules
COPY package.json ./
EXPOSE 3000

CMD ["node", "dist/index.js"]

