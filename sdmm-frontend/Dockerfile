# Dockerfile for Vue 3 SDMM Frontend

FROM node:20-alpine AS build

WORKDIR /usr/src/app

COPY package*.json ./
RUN npm install

COPY . .
RUN npm run build

FROM nginx:alpine

COPY nginx.conf /etc/nginx/nginx.conf

COPY --from=build /usr/src/app/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
