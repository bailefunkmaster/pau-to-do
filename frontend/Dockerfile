FROM node:8 as builder

EXPOSE 8080

WORKDIR /usr/src/app

COPY package.json ./
RUN npm install
RUN npm run-script build 

COPY . .

CMD ["sh", "-c", "npm start" ]

FROM nginx:1.15-alpine

WORKDIR /usr/share/nginx/html

COPY --from=builder /usr/src/app/dist .
