# Builder (Node) Image
FROM node:15-alpine3.10 as builder

RUN apk update && apk add --no-cache make git

# move files into "app" directory
WORKDIR /app
COPY ./front-end .

# install
RUN rm -rf node_modules dist
RUN npm install

# build
RUN npm install -g @angular/cli
RUN ng build --prod

# serve
FROM nginx:1.19-alpine
RUN rm -rf /usr/share/nginx/html/*
COPY --from=builder /app/dist/front-end/* usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]