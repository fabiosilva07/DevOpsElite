FROM node:19.4.0

WORKDIR /app

COPY /app/src/package*.json ./

RUN npm install

COPY /app/src ./

EXPOSE 8080

CMD ["node","server.js"]
