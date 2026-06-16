FROM node:26-alpine3.23 as build

ARG MODE=""

COPY . /app
WORKDIR /app

RUN npm i
RUN npm run build${MODE}

#-------------------------------------------
FROM nginx:alpine

COPY --from=build /app/dist /usr/share/nginx/html
COPY ./nginx/nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80