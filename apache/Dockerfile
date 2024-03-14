FROM node:14.16.0-alpine3.13 AS build
WORKDIR /app
COPY package*.json .
RUN npm install
COPY . .
RUN npm run build


FROM httpd:alpine
COPY --from=build /app/build/ /usr/local/apache2/htdocs/
EXPOSE 80
CMD ["httpd", "-D", "FOREGROUND"]
