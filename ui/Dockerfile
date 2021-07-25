# build environment
FROM node:14-alpine as development

WORKDIR /usr/src/app

COPY package*.json ./

# RUN npm install glob cross-env

RUN npm install

COPY . .

RUN npm run build

# production environment
FROM nginx:stable-alpine as production

COPY --from=development /usr/src/app/dist ./usr/share/nginx/html

COPY --from=development /usr/src/app/nginx/nginx.conf ./etc/nginx/conf.d/default.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]