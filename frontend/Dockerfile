# Base image
FROM node:16 AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Nginx ile serve et
FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
EXPOSE 80
