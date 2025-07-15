# Use Node image to build the app
FROM node:16 AS build

WORKDIR /app

COPY . .

RUN npm install
RUN npm run build

# Use NGINX to serve the Angular app
FROM nginx:alpine

COPY --from=build /app/dist/* /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
