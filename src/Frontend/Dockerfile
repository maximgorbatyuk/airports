### STAGE 1: Build ###
FROM node:13.13.0-alpine AS build
WORKDIR /usr/src/app
COPY package.json package-lock.json ./
RUN npm install
COPY . .
RUN npm run build-prod

### STAGE 2: Run ###
FROM nginx:1.17.1-alpine

RUN rm -rf /usr/share/nginx/html/*
COPY nginx.conf /etc/nginx/nginx.conf
COPY --from=build /usr/src/app/dist/Frontend /usr/share/nginx/html
