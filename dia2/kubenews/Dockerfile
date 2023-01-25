FROM node:18.11.0
WORKDIR /app
COPY ./kubenews/src/package*.json ./
RUN npm install
COPY ./kubenews/src ./
EXPOSE 8080
CMD ["node","server.js"]
