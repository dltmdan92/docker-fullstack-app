FROM node:alpine as node_container
WORKDIR /app
COPY ./package.json ./
RUN npm install
COPY . . 
RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=node_container /app/build /usr/share/nginx/html