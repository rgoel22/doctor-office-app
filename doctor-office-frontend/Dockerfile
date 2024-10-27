FROM node:14 as builder

WORKDIR /usr/src/app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build

EXPOSE 3001

#Stage 2 - Nginx Reverse Proxy
#CMD ["npx", "serve", "build", "-l", "3001"]
FROM nginx

COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf

COPY --from=builder /usr/src/app/build/ /usr/share/nginx/html

