FROM node:14-alpine

WORKDIR /app

COPY package.json /app/

RUN npm install

COPY . /app/

ENV MONGODB_USERNAME=sharan
ENV MONGODB_PASSWORD=password

EXPOSE 80

CMD ["npm", "start"]