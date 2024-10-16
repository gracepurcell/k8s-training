FROM node:alpine

RUN npm i -g json-server

COPY ./db.json /app/db.json

WORKDIR /app

CMD ["json-server", "--watch", "db.json", "--host", "0.0.0.0", "--port", "3000"]
