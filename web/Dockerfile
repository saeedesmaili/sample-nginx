FROM node:lts-alpine as build-stage

RUN npm install -g http-server

WORKDIR /app

COPY package*.json ./

RUN npm cache clean --force && npm install

COPY . .

RUN npm run build

EXPOSE 8080
CMD [ "http-server", "dist" ]

# FROM nginx:stable-alpine as production-stage
# RUN mkdir /app
# RUN rm /etc/nginx/conf.d/default.conf
# COPY nginx.conf /etc/nginx/conf.d
# COPY --from=build-stage /app/dist /etc/nginx/html
# EXPOSE 80
# CMD ["nginx", "-g", "daemon off;"]