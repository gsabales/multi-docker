FROM node:16-alpine as builder
RUN mkdir app
WORKDIR /app
COPY package.json /app/
RUN npm install
COPY . /app/
RUN npm run build

FROM nginx
EXPOSE 80
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
